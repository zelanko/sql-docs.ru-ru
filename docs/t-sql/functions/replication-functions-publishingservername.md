---
title: PUBLISHINGSERVERNAME (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- PUBLISHINGSERVERNAME_TSQL
- PUBLISHINGSERVERNAME
dev_langs:
- TSQL
helpviewer_keywords:
- PUBLISHINGSERVERNAME function
- Publishers [SQL Server replication], names
ms.assetid: e7c278e5-ab23-419e-ab3e-3bb20b0636df
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 178b2cfddf2d7029e731726025d5d47793b37305
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/04/2018
ms.locfileid: "37782795"
---
# <a name="replication-functions---publishingservername"></a>Функции репликации — PUBLISHINGSERVERNAME
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает имя исходного издателя для опубликованной базы данных, участвующей в сеансе зеркального отображения базы данных. Эта функция выполняется на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], который является издателем для базы данных публикации. Она используется для определения первоначального издателя опубликованной базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
PUBLISHINGSERVERNAME()  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **nvarchar**  
  
## <a name="remarks"></a>Remarks  
 Функция PUBLISHINGSERVERNAME используется во всех типах репликации.  
  
 Функция PUBLISHINGSERVERNAME используется в том случае, если в базе данных публикации между издателем и экземпляром участника зеркального отображения существует сеанс зеркального отображения.  
  
 Эта функция должна выполняться в контексте базы данных публикации. При выполнении функции PUBLISHINGSERVERNAME в базе данных публикации на экземпляре зеркального сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращается имя экземпляра издателя, от которого поступила опубликованная база данных. Если эта функция выполняется на экземпляре зеркального сервера для базы данных, которая еще не опубликована или опубликована с экземпляра зеркального сервера после отработки отказа, то возвращается имя данного экземпляра зеркального сервера. Если эта функция выполняется на экземпляре исходного издателя, то возвращается имя этого издателя.  
  
## <a name="see-also"></a>См. также:  
 [Зеркальное отображение и репликация баз данных (SQL Server)](../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)   
 [Функции репликации (Transact-SQL)](http://msdn.microsoft.com/library/53702dee-de58-47d5-a552-7f32000f77d4)  
  
  
