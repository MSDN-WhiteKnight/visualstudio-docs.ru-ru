---
title: Пошаговое руководство. Сохранение пользовательских параметров на начальной странице | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 79a54867044961d972e2ded452958d2463038e7d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318523"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>Пошаговое руководство. Сохранить настройки пользователя на начальной странице

Вы можете сохранить пользовательские параметры на начальной странице. Перечисленные в этом пошаговом руководстве, можно создать элемент управления, который сохраняет параметр в реестр, когда пользователь нажимает кнопку и затем получает задание каждый раз при загрузке страницы запуска. Шаблон проекта начальной страницы включает настраиваемый пользовательский элемент управления, и запустить страницу XAML по умолчанию вызывает этот элемент управления, у вас нет сам изменение начальной страницы.

Хранилище параметров, экземпляр которого создается в этом пошаговом руководстве является экземпляром класса <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> интерфейс, который считывает и записывает в следующий раздел реестра при вызове: **HKCU\Software\Microsoft\VisualStudio\14.0\\\<имя_коллекции >**

При работе в экспериментальном экземпляре Visual Studio, в хранилище параметров считывает и записывает **HKCU\Software\Microsoft\VisualStudio\14.0Exp\\\<имя_коллекции >.**

Дополнительные сведения о том, как сохранение параметров см. в разделе [расширение пользовательские настройки и параметры](../extensibility/extending-user-settings-and-options.md).

## <a name="prerequisites"></a>Предварительные требования

> [!NOTE]
> Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).
>
> Шаблон проекта начальной страницы можно загрузить с помощью **Диспетчер расширений**.

## <a name="set-up-the-project"></a>Настройка проекта

1. Создайте проект начальной страницы, как описано в [Создание настраиваемой начальной страницы](creating-a-custom-start-page.md). Назовите проект **SaveMySettings**.

2. В **обозревателе решений**, добавьте следующие ссылки на сборки в проект StartPageControl:

    - EnvDTE

    - EnvDTE80

    - Microsoft.VisualStudio.OLE.Interop

    - Microsoft.VisualStudio.Shell.Interop.11.0

3. Откройте *файл MyControl.xaml*.

4. XAML, в области верхнего уровня <xref:System.Windows.Controls.UserControl> определение элемента, добавьте следующее объявление события после объявления пространств имен.

    ```xml
    Loaded="OnLoaded"
    ```

5. В области конструктора щелкните основную область элемента управления и нажмите клавишу **удалить**.

     Этот шаг удаляет <xref:System.Windows.Controls.Border> элемент и все ресурсы в ней и оставляет уровня только верхние <xref:System.Windows.Controls.Grid> элемент.

6. Из **элементов**, перетащите <xref:System.Windows.Controls.StackPanel> элемента управления в сетку.

7. Теперь перетащите <xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.TextBox>и кнопка для <xref:System.Windows.Controls.StackPanel>.

8. Добавить **x: Name** для атрибута <xref:System.Windows.Controls.TextBox>и `Click` событие для <xref:System.Windows.Controls.Button>, как показано в следующем примере.

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>Реализация пользовательского элемента управления

1. Щелкните правой кнопкой мыши в области XAML `Click` атрибут <xref:System.Windows.Controls.Button> элемент, а затем щелкните **к обработчику событий**.

     Это приведет к открытию *MyControl.xaml.cs*и создает обработчик заглушки для `Button_Click` событий.

2. Добавьте следующий `using` инструкции в начало файла.

     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]

3. Добавьте закрытый `SettingsStore` свойства, как показано в следующем примере.

    ```csharp
    private IVsWritableSettingsStore _settingsStore = null;
    private IVsWritableSettingsStore SettingsStore
    {
        get
        {
            if (_settingsStore == null)
            {
                // Get a reference to the DTE from the DataContext.
                var typeDescriptor = DataContext as ICustomTypeDescriptor;
                var propertyCollection = typeDescriptor.GetProperties();
                var dte = propertyCollection.Find("DTE", false).GetValue(
                    DataContext) as DTE2;

                // Get the settings manager from the DTE.
                var serviceProvider = new ServiceProvider(
                    (Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);
                var settingsManager = serviceProvider.GetService(
                    typeof(SVsSettingsManager)) as IVsSettingsManager;

                // Write the user settings to _settingsStore.
                settingsManager.GetWritableSettingsStore(
                    (uint)__VsSettingsScope.SettingsScope_UserSettings,
                    out _settingsStore);
            }
            return _settingsStore;
        }
    }
    ```

     Во-первых, это свойство возвращает ссылку на <xref:EnvDTE80.DTE2> интерфейс, который содержит модель объектов автоматизации, из <xref:System.Windows.FrameworkElement.DataContext%2A> пользовательский элемент управления, а затем использует DTE для получения экземпляра <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> интерфейс. Затем он использует этот экземпляр для возвращения параметры текущего пользователя.

4. Заполните `Button_Click` событие следующим образом.

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {
        int exists = 0;
        SettingsStore.CollectionExists("MySettings", out exists);
        if (exists != 1)
        {
            SettingsStore.CreateCollection("MySettings");
        }
        SettingsStore.SetString("MySettings", "MySetting", txtblk.Text);
    }
    ```

     Записывает содержимое текстового поля к полю «MySetting» в коллекции «Мои параметры» в реестре. Если коллекция не существует, он создается.

5. Добавьте следующий обработчик для `OnLoaded` событий пользовательского элемента управления.

    ```csharp
    private void OnLoaded(Object sender, RoutedEventArgs e)
    {
        string value;
        SettingsStore.GetStringOrDefault(
            "MySettings", "MySetting", "", out value);
        txtblk.Text = value;
    }
    ```

     Этот код задает текст надписи на текущее значение «MySetting».

6. Создание пользовательского элемента управления.

7. В **обозревателе решений**откройте *source.extension.vsixmanifest*.

8. В редакторе манифеста задайте **название продукта** для **сохранить мои параметры начальной страницы**.

     Эта функция задает имя начальной страницы, он будет отображаться в **настроить начальную страницу** в списке **параметры** диалоговое окно.

9. Построение *StartPage.xaml*.

## <a name="test-the-control"></a>Тестирование элемента управления

1. Нажмите клавишу **F5**.

     Откроется экспериментальный экземпляр Visual Studio.

2. В экспериментальном экземпляре на **средства** меню, щелкните **параметры**.

3. В **среды** узел, щелкните **запуска**, а затем в **настроить начальную страницу** выберите **[установленных расширений] сохранить мои параметры начальной страницы** .

     Нажмите кнопку **ОК**.

4. Закройте начальной страницы, если он открыт, а затем на **представление** меню, щелкните **начальная страница**.

5. На начальной странице щелкните **MyControl** вкладки.

6. В текстовом поле введите **Cat**, а затем нажмите кнопку **сохранить Мои параметр**.

7. Закройте начальной страницы и откройте его снова.

     Слово «Cat» должно отображаться в текстовом поле.

8. Замените слово «Cat» слово «Dog». Не нажимайте кнопку.

9. Закройте начальной страницы и откройте его снова.

     Слово «Dog» должны отображаться в текстовом поле, несмотря на то, что не был сохранен параметр так, как Visual Studio будет хранить окна инструментов в памяти, даже если они будут закрыты, пока не закроет самой среды Visual Studio.

10. Закройте экспериментальный экземпляр Visual Studio.

11. Нажмите клавишу **F5** Чтобы снова открыть экспериментальный экземпляр.

12. Слово «Cat» должно отображаться в текстовом поле.

## <a name="next-steps"></a>Следующие шаги

Вы можете изменить этот пользовательский элемент управления для сохранения и извлечения любое количество настраиваемых параметров с помощью различных значений из разных обработчика событий для получения и задания `SettingsStore` свойство. Пока вы используете другой `propertyName` параметра для каждого вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>, значения не перезаписывайте друг с другом в реестре.

## <a name="see-also"></a>См. также

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [Добавление команд Visual Studio на начальную страницу](../extensibility/adding-visual-studio-commands-to-a-start-page.md)