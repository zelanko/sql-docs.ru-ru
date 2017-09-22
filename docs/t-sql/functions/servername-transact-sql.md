---
title: "@@SERVERNAME (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@SERVERNAME'
- '@@SERVERNAME_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@SERVERNAME function'
- local servers [SQL Server]
ms.assetid: b0ef33fb-954a-4294-b05b-a87c14ce25a3
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: 93d03e11df97075b2d608d7bfcc4e234c37971cd
ms.contentlocale: ru-ru
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40servername-transact-sql"></a>& #x 40; & #x 40; Имя сервера (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает имя локального сервера, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
@@SERVERNAME  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **nvarchar**  
  
## <a name="remarks"></a>Замечания  
 Программа установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] присваивает серверу имя компьютера. Чтобы изменить имя сервера, используйте **sp_addserver**, а затем перезапустите [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 С несколькими экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установленных @@SERVERNAME возвращает сведения об имени следующие локального сервера, если имя локального сервера не был изменен с момента установки.  
  
|Экземпляр|Информация о сервере|  
|--------------|------------------------|  
|Экземпляр по умолчанию|"*servername*"|  
|Именованный экземпляр|"*servername*\\*instancename*"|  
|экземпляр отказоустойчивого кластера — экземпляр по умолчанию|"*имя_виртуального_сервера*"|  
|экземпляр отказоустойчивого кластера — именованный экземпляр|"*имя_виртуального_сервера*\\*instancename*"|  
  
 Несмотря на то что @@SERVERNAME функции и свойство SERVERNAME функции SERVERPROPERTY могут возвращать строки в похожих форматах, данные могут быть разными. Свойство SERVERNAME автоматически сообщает об изменениях сетевого имени компьютера.  
  
 Напротив, @@SERVERNAME таких изменениях не сообщает. @@SERVERNAME об изменениях имени локального сервера с помощью **sp_addserver** или **sp_dropserver** хранимой процедуры.  
  
## <a name="examples"></a>Примеры  
 Следующий пример демонстрирует использование процедуры `@@SERVERNAME`.  
  
```  
SELECT @@SERVERNAME AS 'Server Name'  
```  
  
 Ниже приводится образец результирующего набора.  
  
```  
Server Name  
---------------------------------  
ACCTG  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции настройки (Transact-SQL)](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [SERVERPROPERTY (Transact-SQL)](../../t-sql/functions/serverproperty-transact-sql.md)   
 [sp_addserver &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)  
  
  

