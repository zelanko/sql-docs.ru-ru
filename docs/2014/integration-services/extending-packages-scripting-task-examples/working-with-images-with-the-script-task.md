---
title: Работа с изображениями в задаче "Скрипт" | Документы Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- graphics [Integration Services]
- Script task [Integration Services], images
- Drawing namespace
- images [Integration Services]
- SSIS Script task, images
- Script task [Integration Services], examples
- thumbnails [Integration Services]
- System.Drawing namespace
- JPEG format [Integration Services]
- .jpeg files
ms.assetid: 74aeb7ab-51b2-4b9f-84ee-0b46a7908ab9
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 413d0d42ce629076488b5971408df25ca0ce9d1e
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84968444"
---
# <a name="working-with-images-with-the-script-task"></a>Работа с изображениями в задаче «Скрипт»
  База данных продуктов или пользователи часто содержат изображения в дополнение к тексту и числовым данным. Пространство имен `System.Drawing` платформы Microsoft .NET Framework предоставляет классы для управления изображениями.  
  
 [Пример 1. Преобразование изображений в формат JPEG](#example1)  
  
 [Пример 2. Создание и сохранение уменьшенных представлений изображений](#example2)  
  
> [!NOTE]  
>  Если нужно создать задачу, которую будет удобно использовать в нескольких пакетах, рекомендуется начать разработку пользовательской задачи с этого образца задачи «Скрипт». Дополнительные сведения см. в разделе [Разработка пользовательской задачи](../extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
##  <a name="example-1-description-convert-images-to-jpeg-format"></a><a name="example1"></a> Описание примера 1. Преобразование изображений в формат JPEG  
 В следующем примере открывается указанный переменной файл изображения. Затем он сохраняется как сжатый JPEG-файл с использованием кодировщика. Код для получения данных кодировщика инкапсулирован в закрытой функции.  
  
#### <a name="to-configure-this-script-task-example-for-use-with-a-single-image-file"></a>Настройка этого примера задачи «Скрипт» для работы с одним файлом изображения  
  
1.  Создайте строковую переменную с именем `CurrentImageFile` и задайте в качестве ее значения путь и имя существующего файла изображения.  
  
2.  На странице **Скрипт** в **редакторе задачи "Скрипт**" добавьте `CurrentImageFile` переменную в `ReadOnlyVariables` свойство.  
  
3.  В проекте скрипта добавьте ссылку на пространство имен `System.Drawing`.  
  
4.  Добавьте в код инструкции `Imports`, чтобы импортировать пространства имен `System.Drawing` и `System.IO`.  
  
#### <a name="to-configure-this-script-task-example-for-use-with-multiple-image-files"></a>Настройка этого примера задачи «Скрипт» для работы с несколькими файлами изображения  
  
1.  Поместите задачу «Скрипт» в контейнер «цикл по каждому элементу».  
  
2.  На странице **Коллекция** окна **Редактор циклов по каждому элементу** выберите **Перечислитель с циклом по каждому файлу** в качестве перечислителя и укажите путь и маску исходных файлов, например "*.bmp".  
  
3.  На странице **Сопоставления переменной** сопоставьте переменную `CurrentImageFile` с индексом 0. Эта переменная передает текущее имя файла в задачу «Скрипт» на каждом проходе перечислителя.  
  
    > [!NOTE]  
    >  Эти шаги выполняются дополнительно к шагам, перечисленным в процедуре для использования одного файла изображения.  
  
### <a name="example-1-code"></a>Код примера 1  
  
```vb  
Public Sub Main()  
  
    'Create and initialize variables.  
    Dim currentFile As String  
    Dim newFile As String  
    Dim bmp As Bitmap  
    Dim eps As New Imaging.EncoderParameters(1)  
    Dim ici As Imaging.ImageCodecInfo  
    Dim supportedExtensions() As String = _  
        {".BMP", ".GIF", ".JPG", ".JPEG", ".EXIF", ".PNG", _  
        ".TIFF", ".TIF", ".ICO", ".ICON"}  
  
    Try  
        'Store the variable in a string for local manipulation.  
        currentFile = Dts.Variables("CurrentImageFile").Value.ToString  
        'Check the extension of the file against a list of  
        'files that the Bitmap class supports.  
        If Array.IndexOf(supportedExtensions, _  
            Path.GetExtension(currentFile).ToUpper) > -1 Then  
  
            'Load the file.  
            bmp = New Bitmap(currentFile)  
  
            'Calculate the new name for the compressed image.  
            'Note: This will overwrite existing JPEGs.  
            newFile = Path.Combine( _  
                Path.GetDirectoryName(currentFile), _  
                String.Concat(Path.GetFileNameWithoutExtension(currentFile), _  
                ".jpg"))  
  
            'Specify the compression ratio (0=worst quality, 100=best quality).  
            eps.Param(0) = New Imaging.EncoderParameter( _  
                Imaging.Encoder.Quality, 75)  
  
            'Retrieve the ImageCodecInfo associated with the jpeg format.  
            ici = GetEncoderInfo("image/jpeg")  
  
            'Save the file, compressing it into the jpeg encoding.  
            bmp.Save(newFile, ici, eps)  
        Else  
            'The file is not supported by the Bitmap class.  
            Dts.Events.FireWarning(0, "Image Resampling Sample", _  
                "File " & currentFile & " is not a supported format.", _  
                "", 0)  
         End If  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        'An error occurred.  
        Dts.Events.FireError(0, "Image Resampling Sample", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
  
Private Function GetEncoderInfo(ByVal mimeType As String) As Imaging.ImageCodecInfo  
  
    'The available image codecs are returned as an array,  
    'which requires code to iterate until the specified codec is found.  
  
    Dim count As Integer  
    Dim encoders() As Imaging.ImageCodecInfo  
  
    encoders = Imaging.ImageCodecInfo.GetImageEncoders()  
  
    For count = 0 To encoders.Length  
        If encoders(count).MimeType = mimeType Then  
            Return encoders(count)  
        End If  
    Next  
  
    'This point is only reached if a codec is not found.  
    Err.Raise(513, "Image Resampling Sample", String.Format( _  
        "The {0} codec is not available. Unable to compress file.", _  
            mimeType))  
    Return Nothing  
  
End Function  
  
```  
  
##  <a name="example-2-description-create-and-save-thumbnail-images"></a><a name="example2"></a> Описание примера 2. Создание и сохранение уменьшенных представлений изображений  
 В следующем примере открывается файл изображения, заданный переменной, создается уменьшенное представление изображения с сохранением постоянной пропорции и сохраняется уменьшенное представление с измененным именем файла. Код для вычисления высоты и ширины уменьшенного представления с сохранением постоянной пропорции инкапсулирован в закрытой подпрограмме.  
  
#### <a name="to-configure-this-script-task-example-for-use-with-a-single-image-file"></a>Настройка этого примера задачи «Скрипт» для работы с одним файлом изображения  
  
1.  Создайте строковую переменную с именем `CurrentImageFile` и задайте в качестве ее значения путь и имя существующего файла изображения.  
  
2.  Создайте также целочисленную переменную `MaxThumbSize` и присвойте значение в пикселях, например 100.  
  
3.  На странице **Скрипт** в **редакторе задачи «Скрипт**» добавьте обе переменные в `ReadOnlyVariables` свойство.  
  
4.  В проекте скрипта добавьте ссылку на пространство имен `System.Drawing`.  
  
5.  Добавьте в код инструкции `Imports`, чтобы импортировать пространства имен `System.Drawing` и `System.IO`.  
  
#### <a name="to-configure-this-script-task-example-for-use-with-multiple-image-files"></a>Настройка этого примера задачи «Скрипт» для работы с несколькими файлами изображения  
  
1.  Поместите задачу «Скрипт» в контейнер «цикл по каждому элементу».  
  
2.  На странице **Коллекция** окна **Редактор циклов по каждому элементу** выберите **Перечислитель с циклом по каждому файлу** в качестве **перечислителя** и укажите путь и маску исходных файлов, например "*.jpg".  
  
3.  На странице **Сопоставления переменной** сопоставьте переменную `CurrentImageFile` с индексом 0. Эта переменная передает текущее имя файла в задачу «Скрипт» на каждом проходе перечислителя.  
  
    > [!NOTE]  
    >  Эти шаги выполняются дополнительно к шагам, перечисленным в процедуре для использования одного файла изображения.  
  
### <a name="example-2-code"></a>Код примера 2  
  
```vb  
Public Sub Main()  
  
    Dim currentImageFile As String  
    Dim currentImage As Image  
    Dim maxThumbSize As Integer  
    Dim thumbnailImage As Image  
    Dim thumbnailFile As String  
    Dim thumbnailHeight As Integer  
    Dim thumbnailWidth As Integer  
  
    currentImageFile = Dts.Variables("CurrentImageFile").Value.ToString  
    thumbnailFile = Path.Combine( _  
        Path.GetDirectoryName(currentImageFile), _  
        String.Concat(Path.GetFileNameWithoutExtension(currentImageFile), _  
        "_thumbnail.jpg"))  
  
    Try  
        currentImage = Image.FromFile(currentImageFile)  
  
        maxThumbSize = CType(Dts.Variables("MaxThumbSize").Value, Integer)  
        CalculateThumbnailSize( _  
            maxThumbSize, currentImage, thumbnailWidth, thumbnailHeight)  
  
        thumbnailImage = currentImage.GetThumbnailImage( _  
           thumbnailWidth, thumbnailHeight, Nothing, Nothing)  
        thumbnailImage.Save(thumbnailFile)  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        Dts.Events.FireError(0, "Script Task Example", _  
        ex.Message & ControlChars.CrLf & ex.StackTrace, _  
        String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
  
Private Sub CalculateThumbnailSize( _  
    ByVal maxSize As Integer, ByVal sourceImage As Image, _  
    ByRef thumbWidth As Integer, ByRef thumbHeight As Integer)  
  
    If sourceImage.Width > sourceImage.Height Then  
        thumbWidth = maxSize  
        thumbHeight = CInt((maxSize / sourceImage.Width) * sourceImage.Height)  
    Else  
        thumbHeight = maxSize  
        thumbWidth = CInt((maxSize / sourceImage.Height) * sourceImage.Width)  
    End If  
  
End Sub  
```  
  
```csharp  
bool ThumbnailCallback()  
        {  
            return false;  
        }  
        public void Main()  
        {  
  
            string currentImageFile;  
            Image currentImage;  
            int maxThumbSize;  
            Image thumbnailImage;  
            string thumbnailFile;  
            int thumbnailHeight = 0;  
            int thumbnailWidth = 0;  
  
            currentImageFile = Dts.Variables["CurrentImageFile"].Value.ToString();  
            thumbnailFile = Path.Combine(Path.GetDirectoryName(currentImageFile), String.Concat(Path.GetFileNameWithoutExtension(currentImageFile), "_thumbnail.jpg"));  
  
            try  
            {  
  
                currentImage = Image.FromFile(currentImageFile);  
  
                maxThumbSize = (int)Dts.Variables["MaxThumbSize"].Value;  
                CalculateThumbnailSize(maxThumbSize, currentImage, ref thumbnailWidth, ref thumbnailHeight);  
  
                Image.GetThumbnailImageAbort myCallback = new Image.GetThumbnailImageAbort(ThumbnailCallback);  
  
                thumbnailImage = currentImage.GetThumbnailImage(thumbnailWidth, thumbnailHeight, ThumbnailCallback, IntPtr.Zero);  
                thumbnailImage.Save(thumbnailFile);  
                Dts.TaskResult = (int)ScriptResults.Success;  
            }  
            catch (Exception ex)  
            {  
                Dts.Events.FireError(0, "Script Task Example", ex.Message + "\r" + ex.StackTrace, String.Empty, 0);  
                Dts.TaskResult = (int)ScriptResults.Failure;  
            }  
  
        }  
  
        private void CalculateThumbnailSize(int maxSize, Image sourceImage, ref int thumbWidth, ref int thumbHeight)  
        {  
  
            if (sourceImage.Width > sourceImage.Height)  
            {  
                thumbWidth = maxSize;  
                thumbHeight = (int)(sourceImage.Height * maxSize / sourceImage.Width);  
            }  
            else  
            {  
                thumbHeight = maxSize;  
                thumbWidth = (int)(sourceImage.Width * maxSize / sourceImage.Height);  
  
            }  
  
        }  
  
```  
  
![Значок Integration Services (маленький)](../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
  
