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
manager: craigg
ms.openlocfilehash: 991757d1bfeae8ecc0dec3a69d82c3dcab6415b1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62914651"
---
# <a name="mssqlserver_33129"></a>MSSQLSERVER_33129
    
## <a name="details"></a>Сведения  
  
|||  
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
  
  
