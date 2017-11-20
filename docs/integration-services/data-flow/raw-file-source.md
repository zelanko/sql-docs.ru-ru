---
title: "Исходный необработанный файл | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.rawfilesource.f1
- sql13.dts.designer.rawfilesourceconnectionmanager.f1
- sql13.dts.designer.rawfilesourcecolumns.f1
helpviewer_keywords:
- sources [Integration Services], Raw File
- raw data [Integration Services]
- Raw File source
ms.assetid: 5b4daea5-7f76-4674-aa77-0a79f9f97f7d
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 7d5bc198ae3082c1b79a3a64637662968b0748b2
ms.openlocfilehash: 14608c3bbf570ecfa4cbc0d45d2961ea7ab48a4d
ms.contentlocale: ru-ru
ms.lasthandoff: 08/17/2017

---
# <a name="raw-file-source"></a>источник «Необработанный файл»
  Источник «Необработанный файл» считывает необработанные данные из файла. Поскольку данные представлены в собственном формате источника, их преобразование не требуется. Также практически не требуется синтаксический анализ. Это означает, что источник необработанных файлов в состоянии считывать данные быстрее, чем другие источники, такие как источник «Неструктурированный файл» и источник «OLE DB».  
  
 Источник «Необработанный файл» используется для извлечения необработанных данных, записанных ранее назначением «Необработанный файл». Вы можете также указать источник «Необработанный файл», указывающий на пустой необработанный файл, содержащий только столбцы (файл только с метаданными). Можно использовать назначение «Необработанный файл» для создания файла только с метаданными без необходимости запускать пакет. Дополнительные сведения см. в статье [Raw File Destination](../../integration-services/data-flow/raw-file-destination.md).  
  
 В формате необработанного файла содержатся сведения о сортировке. Назначение «Необработанный файл» сохраняет все сведения о сортировке, включая флаги сравнения для строковых столбцов. Источник «Необработанный файл» считывает и учитывает сведения о сортировке. С помощью расширенного редактора можно настроить источник «Необработанный файл» так, что флаги сортировки в файле не будут учитываться. Дополнительные сведения о флагах сравнения см. в разделе [Comparing String Data](../../integration-services/data-flow/comparing-string-data.md).  
  
 Для настройки необработанного файла необходимо указать имя файла, который считывается источником «Необработанный файл».  
  
> [!NOTE]  
>  Данный источник не использует диспетчер соединений.  
  
 Этот источник имеет один выход. Вывод ошибок не поддерживается.  
  
## <a name="configuration-of-the-raw-file-source"></a>Настройка источника «Необработанный файл»  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Диалоговое окно **Расширенный редактор** содержит свойства, которые можно установить с помощью программных средств. Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Общие свойства](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Пользовательские свойства необработанного файла](../../integration-services/data-flow/raw-file-custom-properties.md)  
  
## <a name="related-tasks"></a>Связанные задачи  
 Дополнительные сведения о настройке свойств компонента см. в разделе [Установление свойств компонента потока данных](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## <a name="related-content"></a>См. также  
  
-   Запись в блоге [Необработанные файлы ― это здорово](http://www.sqlservercentral.com/blogs/stratesql/archive/2011/1/1/31-days-of-ssis-_1320_-raw-files-are-awesome-_2800_1_2F00_31_2900_.aspx)на сайте sqlservercentral.com  
  
## <a name="raw-file-source-editor-connection-manager-page"></a>Редактор источника «Необработанный файл» (страница «Диспетчер соединений»)
  Источник «Необработанный файл» считывает необработанные данные из файла. Поскольку данные представлены в собственном формате источника, их преобразование не требуется. Также практически не требуется синтаксический анализ.   
## <a name="raw-file-source-editor-columns-page"></a>Редактор источника «Необработанный файл»  (страница "Столбцы")
  Источник «Необработанный файл» считывает необработанные данные из файла. Поскольку данные представлены в собственном формате источника, их преобразование не требуется. Также практически не требуется синтаксический анализ.   
## <a name="see-also"></a>См. также:  
 [Raw File Destination](../../integration-services/data-flow/raw-file-destination.md)   
 [Поток данных](../../integration-services/data-flow/data-flow.md)  
  
  

