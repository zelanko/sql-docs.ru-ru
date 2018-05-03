---
title: Настройка DataFactory | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- DataFactory customization in RDS [ADO]
ms.assetid: 86d77985-a0d0-405a-8587-c85a20540a0e
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 943deaa40e36ae099ca810df1c3a884fe2b937d1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="datafactory-customization"></a>Настройка DataFactory
Служба удаленных данных (RDS) позволяет легко осуществлять доступ к данным в системе трехуровневой клиент сервер. Клиентский элемент управления данных указывает параметры строки подключения и команды для выполнения запроса на удаленный источник данных или строку подключения и [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта параметров для выполнения обновлений.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Параметры передаются программе server на выполнение операции доступа к данным на удаленный источник данных. Служб удаленных рабочих СТОЛОВ предоставляет программу server по умолчанию, которая называется [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) объекта. **RDSServer.DataFactory** возвращает объект, любой **записей** объект, являющийся результатом запроса клиенту.  
  
 Тем не менее **RDSServer.DataFactory** будут ограничены выполнением запросов и обновлений. Не удается выполнить все проверки или обработки строки соединения или команды.  
  
 При использовании ADO, можно указать, что **DataFactory** работают совместно с другим типом сервера программу, которая называется *обработчик*. Обработчик, до их использования для доступа к источнику данных, можно изменить подключение клиента и командной строки. Кроме того обработчик можно принудительно задать права доступа, которые управляют возможности клиента для чтения и записи данных в источнике данных.  
  
 В подразделах данного файла настройки задаются параметры, используемые для изменения параметров клиента и права доступа обработчика.  
  
 Следующие разделы содержат сведения о настройке **DataFactory** объекта.  
  
-   [Общие сведения о файле настроек](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)  
  
-   [Настройка раздела подключения файла](../../../ado/guide/remote-data-service/customization-file-connect-section.md)  
  
-   [Настройка раздела SQL файла](../../../ado/guide/remote-data-service/customization-file-sql-section.md)  
  
-   [Настройка раздела UserList файла](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)  
  
-   [Настройка раздела журналов файла](../../../ado/guide/remote-data-service/customization-file-logs-section.md)  
  
-   [Требуемые параметры клиента](../../../ado/guide/remote-data-service/required-client-settings.md)  
  
-   [Запись собственного настраиваемого обработчика](../../../ado/guide/remote-data-service/writing-your-own-customized-handler.md)


