---
title: SMALLDATETIMEFROMPARTS (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SMALLDATETIMEFROMPARTS
- SMALLDATETIMEFROMPARTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SMALLDATETIMEFROMPARTS function
ms.assetid: 7467fdab-e588-419c-9e29-42caec34a9ea
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7b435d9e02df33d0b7c26029106095680ab881b4
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43072825"
---
# <a name="smalldatetimefromparts-transact-sql"></a>SMALLDATETIMEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Возвращает значение **smalldatetime**, соответствующее указанной дате и времени.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SMALLDATETIMEFROMPARTS ( year, month, day, hour, minute )  
```  
  
## <a name="arguments"></a>Аргументы  
 *year*  
 Целочисленное выражение, задающее год.  
  
 *month*  
 Целочисленное выражение, задающее месяц.  
  
 *day*  
 Целочисленное выражение, задающее день.  
  
 *hour*  
 Целочисленное выражение, задающее часы.  
  
 *minute*  
 Целочисленное выражение, задающее минуты.  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **smalldatetime**  
  
## <a name="remarks"></a>Remarks  
 Эта функция действует как конструктор полностью инициализированного значения **smalldatetime**. Если аргументы недопустимы, то возникает ошибка. Если требуемые аргументы имеют значение NULL, возвращается NULL.  
  
 Для серверов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и выше данная функция может быть удаленной. Она не может быть удаленной для серверов с версией ниже [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="examples"></a>Примеры  
  
```  
SELECT SMALLDATETIMEFROMPARTS ( 2010, 12, 31, 23, 59 ) AS Result  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------------------  
2011-01-01 00:00:00  
  
(1 row(s) affected)  
```  
  

