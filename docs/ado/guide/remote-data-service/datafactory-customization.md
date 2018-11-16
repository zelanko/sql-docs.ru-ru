---
title: Настройка DataFactory | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DataFactory customization in RDS [ADO]
ms.assetid: 86d77985-a0d0-405a-8587-c85a20540a0e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 31434e08443bc533c7e2ae14ed70d6962aea04cf
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2018
ms.locfileid: "51558612"
---
# <a name="datafactory-customization"></a>Настройка DataFactory
Службы удаленных данных (RDS) позволяет легко осуществлять доступ к данным в системе трехуровневой клиент сервер. Параметры строки подключения и команды для выполнения запроса на удаленный источник данных или строка подключения указывает элементу управления данных клиента и [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объект параметров, чтобы выполнить обновление.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Параметры передаются в программу сервера, который выполняет операции доступа к данным на удаленном источнике данных. RDS предоставляет программу по умолчанию сервера под названием [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) объекта. **RDSServer.DataFactory** объект возвращает любой **записей** объект, созданный запросом клиенту.  
  
 Тем не менее **RDSServer.DataFactory** будут ограничены выполнением запросов и обновлений. Не удается выполнить проверку или обработку на строки соединения или команды.  
  
 С помощью ADO можно указать, что **DataFactory** работают в сочетании с помощью другого типа сервера программу под названием *обработчик*. Обработчик можно изменить подключение клиента и командной строки, прежде чем они используются для доступа к источнику данных. Кроме того обработчик может применить права доступа, которые будут регулировать способность клиента для чтения и записи данных в источник данных.  
  
 Параметры, используемые обработчик для изменения параметров клиента и права доступа указаны в разделах файла настройки.  
  
 Следующие разделы содержат дополнительные сведения о настройке **DataFactory** объекта.  
  
-   [Общие сведения о файле настроек](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)  
  
-   [Настройка раздела подключения файла](../../../ado/guide/remote-data-service/customization-file-connect-section.md)  
  
-   [Настройка раздела SQL файла](../../../ado/guide/remote-data-service/customization-file-sql-section.md)  
  
-   [Настройка раздела UserList файла](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)  
  
-   [Настройка раздела журналов файла](../../../ado/guide/remote-data-service/customization-file-logs-section.md)  
  
-   [Требуемые параметры клиента](../../../ado/guide/remote-data-service/required-client-settings.md)  
  
-   [Запись собственного настраиваемого обработчика](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


