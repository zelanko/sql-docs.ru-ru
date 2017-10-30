---
title: "Подключиться к хранилищу больших двоичных объектов (мастер экспорта и импорта SQL Server) | Документы Microsoft"
ms.custom: 
ms.date: 02/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2e482b8-5f90-48c5-93fb-b412ed52659f
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 36b992b5141799d4e168b2e990643e6a515a8d69
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="connect-to-azure-blob-storage-sql-server-import-and-export-wizard"></a>Подключиться к хранилищу больших двоичных объектов (мастер экспорта и импорта SQL Server)
В этом разделе показано, как подключиться к **хранилища больших двоичных объектов** из источника данных **выберите источник данных** или **Выбор назначения** страницы мастера экспорта и импорта SQL Server.

>   [!NOTE]
> Чтобы использовать Azure BLOB-объект источника или назначения, необходимо установить пакет дополнительных компонентов Azure для служб SQL Server Integration Services.
> - Загрузить пакет дополнительных компонентов [Microsoft SQL Server 2016 Integration Services Feature Pack для Azure](https://www.microsoft.com/download/details.aspx?id=49492).
>
> - Дополнительные сведения см. в статье [Пакет дополнительных компонентов Azure для служб Integration Services (SSIS)](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

На следующем снимке экрана показаны параметры настройки для подключения к хранилищу больших двоичных объектов Azure.

![Подключение хранилища BLOB-объектов Azure](../../integration-services/import-export-data/media/azure-blob-storage-connection.png)

## <a name="options-to-specify"></a>Параметры для указания

> [!NOTE]
> Параметры соединения для поставщика данных одинаковы независимо от источника или к назначению хранилища больших двоичных объектов. То есть варианты, вы увидите одинаковы на обоих **выберите источник данных** и **Выбор назначения** страницах мастера.

 **Использовать учетную запись Azure**  
 Укажите, следует ли использовать сетевую учетную запись.
  
 **Имя учетной записи хранения**  
 Введите имя учетной записи хранилища Azure.  
  
**Ключ учетной записи**  
Введите ключ для учетной записи хранилища Azure.  
  
 **Использовать HTTPS**  
 Укажите, какой протокол следует использовать для подключения к учетной записи хранения: HTTP или HTTPS.  
  
 **Использовать локальную учетную запись разработчика**  
 Укажите, следует ли использовать эмулятор хранения на локальном компьютере.  
  
 **Имя контейнера больших двоичных объектов**  
 Выберите контейнер в списке контейнеров хранилища, который доступен в указанной учетной записи хранения.  
  
 **Формат файла большого двоичного объекта**  
 Выберите формат файла Text или Avro.  
  
 **Знак-разделитель столбцов**  
 Если выбран текстовый формат, введите знак-разделитель столбцов.  
  
 **Использовать первую строку в качестве имен столбцов**  
 Укажите, содержит ли первая строка данных имена столбцов.  

## <a name="see-also"></a>См. также:
[Выберите источник данных](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Выбор назначения](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


