---
title: "Редактор диспетчера соединений с Excel | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.excelconnection.f1
helpviewer_keywords:
- Excel Connection Manager Editor
ms.assetid: 7ff097e4-cafb-4885-a898-05b2a46628c1
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3c4060736f824becd05fecceba0b162b45f0fed4
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="excel-connection-manager-editor"></a>редактор диспетчера соединений с Excel
  Диалоговое окно **Редактор диспетчера соединений с Excel** используется для добавления подключения к существующему или новому файлу книги [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] .  
  
 Дополнительные сведения о диспетчере соединений с Excel см. в разделе [Диспетчер соединений с Excel](../../integration-services/connection-manager/excel-connection-manager.md).  
  
## <a name="options"></a>Параметры  
 **Путь к файлу Excel**  
 Введите путь и имя существующего или нового файла книги Excel с расширением XLS.  
  
> [!NOTE]  
>  Подключить защищенный паролем файл Excel нельзя.  
  
> [!WARNING]  
>  **Редактор назначения Excel** автоматически создаст файл Excel при выборе **подключения Excel** , указывающего на новый или несуществующий файл. Затем выберите **Создать** для **имени листа Excel**.  
  
 **Обзор**  
 Для перехода в папку, в которой существует файл Excel или в которой будет создан новый файл, используйте диалоговое окно **Открыть** .  
  
 **Версия Excel**  
 Позволяет указать версию Microsoft Excel, в которой был создан файл.  
  
 **Первая строка содержит имена столбцов**  
 Позволяет указать, содержит ли первая строка данных выбранного листа имена столбцов. По умолчанию значение этого параметра равно **True**.  
  
## <a name="providers-and-drivers-for-microsoft-excel-and-access-file"></a>Поставщики и драйверы для файлов Microsoft Excel и Access  
 Если поставщики OLE DB и драйверы для файлов Microsoft Office еще не установлены, может потребоваться скачать их. Более поздние версии поставщика могут открывать файлы, созданные в более ранних версиях Excel.  
  
 Если на компьютере установлена 32-разрядная версия Office, необходимо установить драйверы для этой версии, а также убедиться, что вы запускаете мастер или создаваемый им пакет служб Integration Services в 32-разрядном режиме.  
  
|Версия Microsoft Office|Загрузить|  
|------------------------------|--------------|  
|2007 г.|[Системный драйвер Office 2007: компоненты подключения к данным](https://www.microsoft.com/download/details.aspx?id=23734)|  
|2010|[Среда выполнения Microsoft Access 2010](https://www.microsoft.com/download/details.aspx?id=10910)|  
|2013|[Среды выполнения Microsoft Access 2013](http://www.microsoft.com/download/details.aspx?id=39358)|  
|2016|[Среда выполнения Microsoft Access 2016](https://www.microsoft.com/download/details.aspx?id=50040)|
  
## <a name="see-also"></a>См. также раздел  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Цикл через Excel файлы и таблицы с помощью цикл](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
  
