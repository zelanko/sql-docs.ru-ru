---
title: catalog.startup | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 271fd405-246a-4852-bfbe-f557241ce6ea
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1625d2a4fb9251d9d6a3722dc4f54578e0dbd8ed
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="catalogstartup"></a>catalog.startup
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Осуществляет обслуживание состояния операций для каталога SSISDB.  
  
 Хранимая процедура исправляет состояние любых пакетов, выполнявшихся в момент отключения экземпляра сервера служб [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
 Предусмотрена возможность включить хранимую процедуру для автоматического выполнения при каждом перезапуске экземпляра сервера [!INCLUDE[ssIS](../../includes/ssis-md.md)], выбрав параметр **Включить автоматическое выполнение хранимой процедуры служб Integration Services при запуске SQL Server** в диалоговом окне **Создание каталога**.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.startup  
```  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ и MODIFY на экземпляр выполнения, разрешения READ и EXECUTE на проект и, при необходимости, разрешения READ на среду, указанную в ссылке  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
  
