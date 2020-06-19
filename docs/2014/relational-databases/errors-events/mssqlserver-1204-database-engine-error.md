---
title: MSSQLSERVER_1204 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1204 (Database Engine error)
ms.assetid: de6ece78-79de-484d-9224-ca0f7645815f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 34b77db95ed4409682b42c0245cf229692b5029a
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84969744"
---
# <a name="mssqlserver_1204"></a>MSSQLSERVER_1204
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|1204|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|LK_OUTOF|  
|Текст сообщения|Экземпляру компонента SQL Server Database Engine не удается получить ресурс LOCK в данный момент времени. Запустите инструкцию повторно, когда число активных пользователей уменьшится. Попросите администратора баз данных проверить конфигурацию блокировки и памяти для данного экземпляра либо выполнить проверку давно выполняющихся транзакций.|  
  
## <a name="explanation"></a>Объяснение  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удается получить ресурс блокировки. Возможны следующие причины этой ошибки.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удается получить дополнительную память операционной системы из-за того, что другие процессы используют ее, либо из-за того, что для сервера установлено значение параметра **max server memory**.  
  
-   Диспетчер блокировок не может использовать более 60 процентов доступной памяти для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="user-action"></a>Действие пользователя  
 Если возникли подозрения, что SQL Server не может выделить необходимое количество памяти, попробуйте следующее.  
  
-   Если другие приложения, кроме SQL Server, используют ресурсы, попытайтесь закрыть эти приложения или запустите их на отдельном сервере. В результате память от других процессов освободится для SQL Server.  
  
-   Если задан параметр max server memory, увеличьте его значение.  
  
 Если есть подозрения, что диспетчер блокировок использовал максимальное количество свободной памяти, определите, какая транзакция удерживает больше всего блокировок, и завершите ее работу. С помощью следующего скрипта можно определить, какая из транзакций удерживает больше всего блокировок:  
  
```  
SELECT request_session_id, COUNT (*) num_locks  
FROM sys.dm_tran_locks  
GROUP BY request_session_id   
ORDER BY count (*) DESC  
```  
  
 Завершите работу сеанса с первым идентификатором с помощью команды KILL.  
  
  
