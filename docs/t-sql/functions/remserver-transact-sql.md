---
title: '@@REMSERVER (Transact-SQL) | Документы Майкрософт'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@REMSERVER'
- '@@REMSERVER_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- logins [SQL Server], remote servers
- remote servers [SQL Server], logins
- '@@REMSERVER function'
ms.assetid: 0bb451a9-3866-4064-963d-b74a2f864049
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0bc401b25b2822b7322c856ed3b2de0e670656b0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67944505"
---
# <a name="x40x40remserver-transact-sql"></a>&#x40;&#x40;REMSERVER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Используйте вместо этого связанные серверы и хранимые процедуры связанных серверов.  
  
 Возвращает имя удаленного сервера базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], как оно указано в учетной записи.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
@@REMSERVER  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **nvarchar(128)**  
  
## <a name="remarks"></a>Remarks  
 @@REMSERVER включает хранимую процедуру для проверки имени сервера базы данных, с которого была запущена процедура.  
  
## <a name="examples"></a>Примеры  
 Следующий пример создает процедуру `usp_CheckServer`, которая возвращает имя удаленного сервера.  
  
```  
CREATE PROCEDURE usp_CheckServer  
AS  
SELECT @@REMSERVER;  
```  
  
 Нижеприведенная хранимая процедура создается на локальном сервере `SEATTLE1`. Пользователь входит на удаленный сервер `LONDON2` и запускает `usp_CheckServer`.  
  
```  
EXEC SEATTLE1...usp_CheckServer;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
---------------  
LONDON2  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции настройки (Transact-SQL)](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [Удаленные серверы](../../database-engine/configure-windows/remote-servers.md)  
  
  
