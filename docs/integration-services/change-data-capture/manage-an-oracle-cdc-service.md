---
description: Manage an Oracle CDC Service
title: Управление службой CDC Oracle | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- createSrv
ms.assetid: 5972cee3-b1a9-4c56-aed6-bdddf84af283
author: chugugrace
ms.author: chugu
ms.openlocfilehash: aea4d1beb0a77e6bc7a0456c3f3437c919698bcd
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "88426076"
---
# <a name="manage-an-oracle-cdc-service"></a>Manage an Oracle CDC Service

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Можно использовать консоль настройки службы CDC для управления конкретной службой CDC.  
  
 **Выбор службы CDC, с которой требуется выполнить действия**  
  
1.  На левой панели консоли настройки службы CDC разверните список **Локальные службы CDC**.  
  
2.  Выберите службу CDC, с которой требуется выполнить действия.  
  
     Также можно щелкнуть правой кнопкой мыши службу CDC, с которой требуется начать работу, и выбрать нужное действие. См. раздел [Что можно сделать с помощью службы CDC Service](../../integration-services/change-data-capture/manage-an-oracle-cdc-service.md#BKMK_WhatcandowithCDCService).  
  
 **OR**  
  
1.  Выберите пункт **Локальные службы CDC** на левой панели консоли настройки службы CDC.  
  
2.  В средней части консоли настройки службы CDC выберите службу, с которой требуется начать работу.  
  
     Также можно щелкнуть правой кнопкой мыши службу CDC, с которой требуется начать работу, и выбрать нужное действие. См. раздел [Что можно сделать с помощью службы CDC Service](../../integration-services/change-data-capture/manage-an-oracle-cdc-service.md#BKMK_WhatcandowithCDCService).  
  
##  <a name="what-can-you-do-with-a-cdc-service"></a><a name="BKMK_WhatcandowithCDCService"></a> Что можно сделать с помощью службы CDC Service  
 При работе со службой CDC можно выполнять следующие действия.  
  
### <a name="delete-the-service"></a>Удаление службы  
 На панели **Действия** в правой стороне консоли настройки службы CDC щелкните **Удалить** , чтобы удалить службу.  
  
 Можно также щелкнуть правой кнопкой мыши службу CDC, которую необходимо удалить, и выбрать команду **Удалить**.  
  
 **Примечание**. Если на момент удаления службы она запущена, перед удалением выполняется ее остановка.  
  
 Чтобы удалить определение службы Windows для Oracle CDC, программе нужен доступ в режиме UPDATE к базе данных MSXDBCDC в соответствующем экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . После нажатия кнопки «ОК» для удаления службы программа попытается выполнить удаление регистрации службы Oracle CDC в базе данных MSXDBCDC. Если программа не может удалить регистрацию службы Oracle CDC, поскольку для нее отсутствуют соответствующие разрешения, то выводит запрос на ввод имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с разрешениями на обновление базы данных MSXDBCDC.  
  
 Дополнительные сведения о вводе данных в диалоговом окне «Подключение к SQL Server» см. в разделе [Connection to SQL Server for Delete](../../integration-services/change-data-capture/connection-to-sql-server-for-delete.md).  
  
### <a name="edit-the-cdc-service-properties"></a>Изменение свойств службы CDC  
 На панели **Действия** в правой стороне консоли настройки службы CDC щелкните пункт **Свойства**.  
  
 Также можно щелкнуть правой кнопкой мыши службу CDC, свойства которой требуется изменить, и выбрать команду **Свойства**.  
  
## <a name="see-also"></a>См. также:  
 [Как управлять локальной службой CDC](../../integration-services/change-data-capture/how-to-manage-a-local-cdc-service.md)  
  
  
