---
title: Управление службой CDC Oracle | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- createSrv
ms.assetid: 5972cee3-b1a9-4c56-aed6-bdddf84af283
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8fb328c6fb7418ad1aa239e63eb537e0857e345c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48073464"
---
# <a name="manage-an-oracle-cdc-service"></a>Manage an Oracle CDC Service
  Можно использовать консоль настройки службы CDC для управления конкретной службой CDC.  
  
 **Выбор службы CDC, с которой требуется выполнить действия**  
  
1.  На левой панели консоли настройки службы CDC разверните список **Локальные службы CDC**.  
  
2.  Выберите службу CDC, с которой требуется выполнить действия.  
  
     Также можно щелкнуть правой кнопкой мыши службу CDC, с которой требуется начать работу, и выбрать нужное действие. См. раздел [Что можно сделать с помощью службы CDC Service](manage-an-oracle-cdc-service.md#bkmk_whatcandowithcdcservice).  
  
 **OR**  
  
1.  Выберите пункт **Локальные службы CDC** на левой панели консоли настройки службы CDC.  
  
2.  В средней части консоли настройки службы CDC выберите службу, с которой требуется начать работу.  
  
     Также можно щелкнуть правой кнопкой мыши службу CDC, с которой требуется начать работу, и выбрать нужное действие. См. раздел [Что можно сделать с помощью службы CDC Service](manage-an-oracle-cdc-service.md#bkmk_whatcandowithcdcservice).  
  
##  <a name="BKMK_WhatcandowithCDCService"></a> Что можно сделать с помощью службы CDC Service  
 При работе со службой CDC можно выполнять следующие действия.  
  
### <a name="delete-the-service"></a>Удаление службы  
 На панели **Действия** в правой стороне консоли настройки службы CDC щелкните **Удалить** , чтобы удалить службу.  
  
 Можно также щелкнуть правой кнопкой мыши службу CDC, которую необходимо удалить, и выбрать команду **Удалить**.  
  
 **Примечание**. Если на момент удаления службы она запущена, перед удалением выполняется ее остановка.  
  
 Чтобы удалить определение службы Windows для Oracle CDC, программе нужен доступ в режиме UPDATE к базе данных MSXDBCDC в соответствующем экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . После нажатия кнопки «ОК» для удаления службы программа попытается выполнить удаление регистрации службы Oracle CDC в базе данных MSXDBCDC. Если программа не может удалить регистрацию службы Oracle CDC, поскольку для нее отсутствуют соответствующие разрешения, то выводит запрос на ввод имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с разрешениями на обновление базы данных MSXDBCDC.  
  
 Дополнительные сведения о вводе данных в диалоговом окне «Подключение к SQL Server» см. в разделе [Connection to SQL Server for Delete](connection-to-sql-server-for-delete.md).  
  
### <a name="edit-the-cdc-service-properties"></a>Изменение свойств службы CDC  
 На панели **Действия** в правой стороне консоли настройки службы CDC щелкните пункт **Свойства**.  
  
 Также можно щелкнуть правой кнопкой мыши службу CDC, свойства которой требуется изменить, и выбрать команду **Свойства**.  
  
## <a name="see-also"></a>См. также:  
 [Как управлять локальной службой CDC](how-to-manage-a-local-cdc-service.md)  
  
  
