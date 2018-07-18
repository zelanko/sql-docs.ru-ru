---
title: Подключение к хранилищу BLOB-объектов (мастер импорта и экспорта SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 02/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e2e482b8-5f90-48c5-93fb-b412ed52659f
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6082e9699e213beb44076cb68b7b530c2d083904
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35400186"
---
# <a name="connect-to-azure-blob-storage-sql-server-import-and-export-wizard"></a>Подключение к хранилищу BLOB-объектов (мастер импорта и экспорта SQL Server)
В этом разделе показано, как подключаться к источникам данных **хранилища BLOB-объектов Azure** со страницы **Выбор источника данных** или **Выбор назначения** в мастере импорта и экспорта SQL Server.

>   [!NOTE]
> Чтобы использовать источник или назначение BLOB-объектов Azure, необходимо установить пакет дополнительных компонентов Azure для служб SQL Server Integration Services.
> - Скачать [пакет дополнительных компонентов служб Microsoft SQL Server 2016 Integration Services для Azure](https://www.microsoft.com/download/details.aspx?id=49492).
>
> - Дополнительные сведения см. в статье [Пакет дополнительных компонентов Azure для служб Integration Services (SSIS)](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

На следующем снимке экрана показаны параметры настройки для подключения к хранилищу BLOB-объектов Azure.

![Подключение хранилища BLOB-объектов Azure](../../integration-services/import-export-data/media/azure-blob-storage-connection.png)

## <a name="options-to-specify"></a>Указываемые параметры

> [!NOTE]
> Параметры подключения для этого поставщика данных одинаковы независимо от того, является ли хранилище BLOB-объектов Azure источником или назначением. Таким образом, на страницах **Выбор источника данных** и **Выбор назначения** мастера отображаются одинаковые параметры.

 **Использовать учетную запись Azure**  
 Укажите, следует ли использовать сетевую учетную запись.
  
 **Имя учетной записи хранения**  
 Введите имя учетной записи хранения Azure.  
  
**Ключ учетной записи**  
Введите ключ для учетной записи хранения Azure.  
  
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

## <a name="see-also"></a>См. также раздел
[Выбор источника данных](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Выбор назначения](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)

