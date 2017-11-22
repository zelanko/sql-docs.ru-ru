---
title: "MSSQLSERVER_33129 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 33129 (Database Engine error)
ms.assetid: 83b5f368-f1a1-4a40-9bb6-c77e2dec690f
caps.latest.revision: "7"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 04eea183e0c393c987b6cd9a99dec888c95c8b33
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver33129"></a>MSSQLSERVER_33129
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|33129|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SEC_CANNOT_DISABLE_WIN_GROUP|  
|Текст сообщения|Нельзя использовать параметр ALTER_LOGIN с аргументом DISABLE, чтобы запретить доступ группе Windows.|  
  
## <a name="explanation"></a>Объяснение  
Это сообщение появляется при попытке отключить имя входа группы Windows.  
  
## <a name="user-action"></a>Действие пользователя  
Имя входа группы Windows не может быть отключено. Чтобы временно удалить разрешения на доступ, предоставленные группе Windows, отзовите (REVOKE) разрешение на подключение (CONNECT) у имени входа группы Windows. Пользователи Windows по-прежнему имеют доступ с индивидуальным именем входа или именем входа другой группы Windows. В следующем примере отменяется разрешение на подключение, предоставленное группе учетных записей домена WESTCOAST.  
  
```Transact-SQL  
REVOKE CONNECT TO [WESTCOAST\Accounting];  
```  
  
