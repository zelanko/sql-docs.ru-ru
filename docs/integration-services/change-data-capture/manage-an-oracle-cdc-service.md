---
title: "Управление службой CDC Oracle | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: change-data-capture
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- createSrv
ms.assetid: 5972cee3-b1a9-4c56-aed6-bdddf84af283
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ece331cf561da80bf56df914fec6f42159ade23e
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="manage-an-oracle-cdc-service"></a>Управление службой CDC Oracle
  Можно использовать консоль настройки службы CDC для управления конкретной службой CDC.  
  
 **Выбор службы CDC, с которой требуется выполнить действия**  
  
1.  На левой панели консоли настройки службы CDC разверните список **Локальные службы CDC**.  
  
2.  Выберите службу CDC, с которой требуется выполнить действия.  
  
     Также можно щелкнуть правой кнопкой мыши службу CDC, с которой требуется начать работу, и выбрать нужное действие. См. раздел [What can you do with a CDC Service](../../integration-services/change-data-capture/manage-an-oracle-cdc-service.md#BKMK_WhatcandowithCDCService).  
  
 **или**  
  
1.  Выберите пункт **Локальные службы CDC** на левой панели консоли настройки службы CDC.  
  
2.  В средней части консоли настройки службы CDC выберите службу, с которой требуется начать работу.  
  
     Также можно щелкнуть правой кнопкой мыши службу CDC, с которой требуется начать работу, и выбрать нужное действие. См. раздел [What can you do with a CDC Service](../../integration-services/change-data-capture/manage-an-oracle-cdc-service.md#BKMK_WhatcandowithCDCService).  
  
##  <a name="BKMK_WhatcandowithCDCService"></a> What can you do with a CDC Service  
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
  
## <a name="see-also"></a>См. также  
 [Как управлять локальной службой CDC](../../integration-services/change-data-capture/how-to-manage-a-local-cdc-service.md)  
  
  

