---
title: MSSQLSERVER_33129 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33129 (Database Engine error)
ms.assetid: 83b5f368-f1a1-4a40-9bb6-c77e2dec690f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: aa6bf73b360fae88f241bef06ade80d08f0a5078
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551634"
---
# <a name="mssqlserver_33129"></a>MSSQLSERVER_33129
    
## <a name="details"></a>Сведения  
  
|attribute|Значение|  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|33129|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SEC_CANNOT_DISABLE_WIN_GROUP|  
|Текст сообщения|Нельзя использовать параметр ALTER_LOGIN с аргументом DISABLE, чтобы запретить доступ группе Windows.|  
  
## <a name="explanation"></a>Объяснение  
 Это сообщение появляется при попытке отключить имя входа группы Windows.  
  
## <a name="user-action"></a>Действие пользователя  
 Имя входа группы Windows не может быть отключено. Чтобы временно удалить разрешения на доступ, предоставленные группе Windows, отзовите (REVOKE) разрешение на подключение (CONNECT) у имени входа группы Windows. Пользователи Windows по-прежнему имеют доступ с индивидуальным именем входа или именем входа другой группы Windows. В следующем примере отменяется разрешение на подключение, предоставленное группе учетных записей домена WESTCOAST.  
  
```sql  
REVOKE CONNECT TO [WESTCOAST\Accounting];  
```  
  
  
