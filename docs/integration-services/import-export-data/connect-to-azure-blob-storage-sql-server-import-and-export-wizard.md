---
description: Подключение к хранилищу BLOB-объектов (мастер импорта и экспорта SQL Server)
title: Подключение к хранилищу BLOB-объектов (мастер импорта и экспорта SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 02/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e2e482b8-5f90-48c5-93fb-b412ed52659f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9848ba94687f6f4555492de868f32431b3e1de84
ms.sourcegitcommit: 9be0047805ff14e26710cfbc6e10d6d6809e8b2c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "89042413"
---
# <a name="connect-to-azure-blob-storage-sql-server-import-and-export-wizard"></a>Подключение к хранилищу BLOB-объектов (мастер импорта и экспорта SQL Server)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


В этом разделе показано, как подключаться к источникам данных **хранилища BLOB-объектов Azure** со страницы **Выбор источника данных** или **Выбор назначения** в мастере импорта и экспорта SQL Server.

> [!NOTE]
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
  
 **Используйте протокол HTTPS.**  
 Укажите, какой протокол следует использовать для подключения к учетной записи хранения: HTTP или HTTPS.  
  
 **Use local developer account (Использовать локальную учетную запись разработчика)**  
 Укажите, следует ли использовать эмулятор хранения Azure на локальном компьютере.  
  
 **Имя контейнера больших двоичных объектов**  
 Выберите контейнер в списке контейнеров хранилища, который доступен в указанной учетной записи хранения.  
  
 **Формат файла большого двоичного объекта**  
 Выберите формат файла Text или Avro.  
  
 **Знак-разделитель столбцов**  
 Если выбран текстовый формат, введите знак-разделитель столбцов.  
  
 **Use first row as column names (Использовать первую строку в качестве имен столбцов)**  
 Укажите, содержит ли первая строка данных имена столбцов.  

## <a name="see-also"></a>См. также раздел
[Выбор источника данных](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Выбор назначения](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)

