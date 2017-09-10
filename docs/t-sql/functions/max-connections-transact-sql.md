---
title: "@@MAX_CONNECTIONS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@MAX_CONNECTIONS'
- '@@MAX_CONNECTIONS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- simultaneous connections [SQL Server]
- maximum number of simultaneous user connections
- '@@MAX_CONNECTIONS function'
- connections [SQL Server], simultaneous
- number of simultaneous user connections
ms.assetid: 57eb9f4b-548f-4212-9684-a11d831c4732
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 920bae6fe464d9947ed44236ec13117c55c5cc7d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="maxconnections-transact-sql"></a>@@MAX_CONNECTIONS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает максимально допустимое количество одновременных соединений пользователя с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Возвращаемое значение необязательно является заданным на настоящий момент значением.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
@@MAX_CONNECTIONS  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **integer**  
  
## <a name="remarks"></a>Замечания  
 Фактическое допустимое количество пользовательских соединений также зависит от установленной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и от ограничений, налагаемых приложениями и оборудованием.  
  
 Чтобы перенастроить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] меньшее количество соединений, используйте **sp_configure**.  
  
## <a name="examples"></a>Примеры  
 В ходе выполнения следующего примера возвращается максимально допустимое количество одновременных соединений пользователей с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Предполагается, что экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не настраивался для уменьшения количества соединений.  
  
```  
SELECT @@MAX_CONNECTIONS AS 'Max Connections';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Max Connections  
---------------  
32767            
```  
  
## <a name="see-also"></a>См. также:  
 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Функции конфигурации](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [Настройка параметра конфигурации сервера user connections](../../database-engine/configure-windows/configure-the-user-connections-server-configuration-option.md)  
  
  
