---
title: catalog.startup | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 271fd405-246a-4852-bfbe-f557241ce6ea
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 4d3087f5816b32ffa83876a32a07ccca521c9394
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68038642"
---
# <a name="catalogstartup"></a>catalog.startup 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


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
  
  
