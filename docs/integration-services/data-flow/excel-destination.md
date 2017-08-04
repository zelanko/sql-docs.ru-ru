---
title: "Назначение Excel | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.exceldest.f1
helpviewer_keywords:
- destinations [Integration Services], Excel
- Excel [Integration Services]
ms.assetid: 37c07446-1264-4814-b4f5-9c66d333bb24
caps.latest.revision: 49
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 62feb48c0b05d6f7c8d6b3342b49d9b050113ac3
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="excel-destination"></a>Назначение Excel
  Назначение «Excel» загружает данные в листы или диапазоны в книгах [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel.  
  
## <a name="access-modes"></a>Режимы доступа  
 Назначение «Excel» предоставляет три различных режима доступа к данным для загрузки:  
  
-   Таблица или представление.  
  
-   Таблица или представление, указанные в переменной.  
  
-   Результат выполнения инструкции SQL. Может использоваться параметризированный запрос.  
  
> [!IMPORTANT]  
>  Лист или диапазон в Excel эквивалентны таблице или представлению. Списки доступных таблиц в источнике Excel и редакторах назначения отображают только существующие листы (обозначенные знаком $, добавленным к имени листа, как в имени Лист1$) и именованные диапазоны (обозначенные отсутствием знака $, как в имени Мой_диапазон).  
  
## <a name="usage-considerations"></a>Особенности использования  
 Диспетчер соединений Excel использует поставщик [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB для Jet 4.0, который поддерживает драйвер Excel ISAM (индексированный последовательный метод доступа) для подключения, а также чтения и записи данных в источники данных Excel.  
  
 Во многих имеющихся статьях базы знаний [!INCLUDE[msCoName](../../includes/msconame-md.md)] описывается поведение этого поставщика и драйвера, и хотя эти статьи не относятся к [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и их предшественникам, службам преобразования данных, вам может быть интересно изучить поведение, которое может привести к неожиданным результатам. Общие сведения об использовании и поведении драйвера Excel см. в разделе [Как использовать ADO с данными Excel из Visual Basic или VBA](http://support.microsoft.com/kb/257819).  
  
 При сохранении данных в назначение «Excel» следующее поведение поставщика Jet в сочетании с драйвером Excel может привести к непредвиденным результатам.  
  
-   **Сохранение текстовых данных**. При сохранении значений текстовых данных в назначение «Excel» драйвер Excel предваряет текст в каждой ячейке символом одинарной кавычки ('); это гарантирует, что сохраненные значения будут интерпретироваться как текстовые. При разработке других приложений, которые считывают или обрабатывают сохраненные данные, следует выполнять специальную обработку для символа одинарной кавычки ('), за которым следуют текстовые значения.  
  
     Сведения о том, как избежать включения символа одинарной кавычки, см. в записи блога [Single quote is appended to all strings when data is transformed to excel when using Excel destination data flow component in SSIS package](http://go.microsoft.com/fwlink/?LinkId=400876)на веб-сайте msdn.com.  
  
-   **Сохранение данных типа memo (ntext)**. Чтобы успешно сохранять в столбцы Excel строки, имеющие длину более 255 символов, драйвер должен распознать тип данных целевого столбца как **memo** , а не как **string**. Если в целевой таблице уже содержатся строки данных, то в столбце типа memo в первых нескольких строках, которые проверит драйвер, должен содержаться, по крайней мере, один экземпляр значения, имеющего длину более 255 символов. Если целевая таблица создается во время проектирования пакета или во время выполнения, в инструкции CREATE TABLE необходимо использовать LONGTEXT (или один из его синонимов) в качестве типа данных для столбца типа memo.  
  
-   **Типы данных**. Драйвер Excel распознает только ограниченный набор типов данных. Например, все числовые столбцы воспринимаются как тип double (DT_R8), а все строковые столбцы (кроме столбцов типа memo) воспринимаются как строки в Юникоде длиной 255 символов (DT_WSTR). [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] сопоставляют типы данных Excel следующим образом.  
  
    -   Числовой — с плавающей запятой двойной точности (DT_R8)  
  
    -   Денежный — денежный (DT_CY)  
  
    -   Логический — логический (DT_BOOL)  
  
    -   Дата/время —     **дата/время** (DT_DATE)  
  
    -   Строка — строка в Юникоде длиной 255 символов (DT_WSTR)  
  
    -   Memo — текстовый поток в Юникоде (DT_NTEXT)  
  
-   **Преобразования типов данных и длины по умолчанию**. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] неявное преобразование типов данных не выполняется. Поэтому может потребоваться использование преобразования «Производный столбец» или «Преобразование данных», чтобы выполнить явное преобразование данных до их загрузки в назначение, отличное от Excel, либо выполнить преобразование данных, отличных от данных Excel, до их загрузки в назначение «Excel». В этом случае может оказаться полезным создать исходный пакет с помощью мастера импорта и экспорта, который сам настроит необходимые преобразования. Ниже приведены некоторые примеры преобразований, которые могут потребоваться.  
  
    -   Преобразование между строковыми столбцами Excel в Юникоде и строковыми столбцами в формате с конкретными кодовыми страницами, отличными от Юникода.  
  
    -   Преобразование между строковыми столбцами Excel длиной в 255 символов и строковыми столбцами другой длины.  
  
    -   Преобразование между числовыми столбцами Excel с плавающей запятой двойной точности и числовыми столбцами других типов.  
  
## <a name="configuration-of-the-excel-destination"></a>Настройка назначения Excel  
 Назначение «Excel» использует диспетчер соединений Excel для подключения к источнику данных, а диспетчер соединений определяет файл книги для использования. Дополнительные сведения см. в статье [Excel Connection Manager](../../integration-services/connection-manager/excel-connection-manager.md).  
  
 Назначение «Excel» имеет один обычный вход и один вывод ошибок.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно установить в диалоговом окне **Редактор назначения «Excel»** , см. в одном из следующих разделов:  
  
-   [Редактор назначения "Excel" (страница "Диспетчер соединений")](../../integration-services/data-flow/excel-destination-editor-connection-manager-page.md)  
  
-   [Редактор назначения "Excel" (страница "Сопоставления")](../../integration-services/data-flow/excel-destination-editor-mappings-page.md)  
  
-   [Редактор назначения "Excel" (страница "Вывод ошибок")](../../integration-services/data-flow/excel-destination-editor-error-output-page.md)  
  
 Диалоговое окно **Расширенный редактор** содержит все свойства, которые могут устанавливаться программными средствами. Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Общие свойства](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Пользовательские свойства Excel](../../integration-services/data-flow/excel-custom-properties.md)  
  
 Дополнительные сведения о настройке свойств см. в разделе [Установление свойств компонента потока данных](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
  
-   [Подключение к книге Excel](../../integration-services/connection-manager/connect-to-an-excel-workbook.md)  
  
-   [просматривать файлы и таблицы Excel с помощью контейнера «цикл по каждому элементу»](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
-   [Установление свойств компонента потока данных](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a>См. также  
  
-   Запись в блоге [Excel в службах Integration Services, часть 1 из 3. Соединения и компоненты](http://go.microsoft.com/fwlink/?LinkId=217674)на сайте dougbert.com  
  
-   Запись в блоге [Excel в службах Integration Services, часть 2 из 3. Таблицы и типы данных](http://go.microsoft.com/fwlink/?LinkId=217675)на сайте dougbert.com  
  
-   Запись в блоге [Excel в службах Integration Services, часть 3 из 3. Проблемы и альтернативы](http://go.microsoft.com/fwlink/?LinkId=217676)на сайте dougbert.com  
  
## <a name="see-also"></a>См. также  
 [Источник Excel](../../integration-services/data-flow/excel-source.md)   
 [Службы Integration Services &#40; Службы SSIS &#41; Переменные](../../integration-services/integration-services-ssis-variables.md)   
 [Поток данных](../../integration-services/data-flow/data-flow.md)   
 [Работа с файлами Excel с помощью задачи «скрипт»](../../integration-services/extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)  
  
  
