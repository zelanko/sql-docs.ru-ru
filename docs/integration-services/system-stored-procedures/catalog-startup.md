---
title: "Catalog.Startup | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 271fd405-246a-4852-bfbe-f557241ce6ea
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3a8c89be0541be1861f45240b891d349019a8935
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogstartup"></a>catalog.startup
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Осуществляет обслуживание состояния операций для каталога SSISDB.  
  
 Хранимая процедура исправляет состояние любых пакетов, выполнявшихся в момент отключения экземпляра сервера служб [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
 У вас есть возможность включить хранимую процедуру на автоматический запуск при каждом [!INCLUDE[ssIS](../../includes/ssis-md.md)] перезапуске экземпляра сервера, выбрав **включить автоматическое выполнение служб Integration Services хранимой процедуры при запуске SQL Server** в диалоговом окне **создать каталог** диалоговое окно.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.startup  
```  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ и MODIFY на экземпляр выполнения, разрешения READ и EXECUTE на проект и, при необходимости, разрешения READ на среду, указанную в ссылке  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
  

