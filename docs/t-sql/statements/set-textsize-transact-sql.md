---
title: "SET TEXTSIZE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 04/12/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TEXTSIZE_TSQL
- TEXTSIZE
- SET_TEXTSIZE_TSQL
- SET TEXTSIZE
dev_langs:
- TSQL
helpviewer_keywords:
- SET TEXTSIZE statement
- SELECT statement [SQL Server], text size returned
- size [SQL Server], text and image data
- TEXTSIZE option
- text size returned [SQL Server]
ms.assetid: 787154a6-39a6-4dd6-a6d0-67b4364f95d5
caps.latest.revision: 38
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2d9925b382a7d09722846ca7da583fb92fe4609c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="set-textsize-transact-sql"></a>SET TEXTSIZE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Указывает размер **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, **текст**, **ntext** , и **изображения** данные, возвращаемые инструкцией SELECT.  
  
> [!IMPORTANT]  
>  **ntext**, **текст**, и **изображения** типов данных будет удалена в будущей версии [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Следует избегать использования этих типов данных при новой разработке и запланировать изменение приложений, использующих их в настоящий момент. Вместо них следует использовать типы данных **nvarchar(max)**, **varchar(max)**и **varbinary(max)** .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SET TEXTSIZE { number }   
```  
  
## <a name="arguments"></a>Аргументы  
 *number*  
 Длина **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, **текст**, **ntext**, или **изображения** данных в байтах. *номер* имеет тип integer и максимальное значение 2147483647 (2 ГБ).  Значение-1 означает Неограниченный размер. Значение 0 устанавливает размер в 4 КБ значение по умолчанию.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (10.0 и более поздние версии) и драйвер ODBC для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматического указания `-1` (без ограничений) при подключении.  
  
 **Драйверы, которые старше [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB (версии 9) для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при соединении автоматически устанавливают TEXTSIZE 2147483647.  
  
## <a name="remarks"></a>Замечания  
 Параметр SET TEXTSIZE затрагивает @@TEXTSIZE функции.  
  
 Значение TEXTSIZE устанавливается во время выполнения, а не во время синтаксического анализа.  
  
## <a name="permissions"></a>Permissions  
 Необходимо быть членом роли **public** .  
  
## <a name="see-also"></a>См. также:  
 [@@TEXTSIZE &#40;Transact-SQL&#41;](../../t-sql/functions/textsize-transact-sql.md)   
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

