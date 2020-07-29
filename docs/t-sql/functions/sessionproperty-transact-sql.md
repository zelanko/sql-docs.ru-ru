---
title: SESSIONPROPERTY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SESSIONPROPERTY
- SESSIONPROPERTY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SET statement, SESSIONPROPERTY function
- SESSIONPROPERTY function
- sessions [SQL Server], SET options settings
ms.assetid: 1f3730b4-1495-4d3a-af43-e57952812df9
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 59136d840df4bedb56f9b68f19bca28f2508ff1e
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "87112311"
---
# <a name="sessionproperty-transact-sql"></a>SESSIONPROPERTY (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает параметры SET для сеанса.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SESSIONPROPERTY (option)  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 *Параметр*  
 Текущий параметр для данного сеанса. Аргумент *option* может принимать любое из указанных ниже значений.  
  
|Параметр|Описание|  
|------------|-----------------|  
|ANSI_NULLS|Позволяет задать поведение по стандарту ISO оператора сравнения "равно" (=) и "не равно" (<>) при использовании со значениями NULL.<br /><br /> 1 = включен;<br /><br /> 0 = выключен.|  
|ANSI_PADDING|Определяет, как в столбце сохраняются более короткие значения, чем заданный размер столбца, а также символьные и двоичные значения с завершающими пробелами.<br /><br /> 1 = включен;<br /><br /> 0 = выключен.|  
|ANSI_WARNINGS|Определяет, будет ли при возникновении ряда ситуаций, включая деление на нуль и арифметическое переполнение, применяться совместимое со стандартом ISO правило выведения сообщений об ошибках или предупреждений.<br /><br /> 1 = включен;<br /><br /> 0 = выключен.|  
|ARITHABORT|Определяет, завершен ли запрос, если во время его выполнения возникает ошибка переполнения или деления на нуль.<br /><br /> 1 = включен;<br /><br /> 0 = выключен.|  
|CONCAT_NULL_YIELDS_ NULL|Управляет представлением результатов объединения в виде значений NULL или пустых строковых значений.<br /><br /> 1 = включен;<br /><br /> 0 = выключен.|  
|NUMERIC_ROUNDABORT|Определяет, создаются ли сообщения об ошибках и предупреждения в случаях, когда округление в выражении приводит к потере точности.<br /><br /> 1 = включен;<br /><br /> 0 = выключен.|  
|QUOTED_IDENTIFIER|Указывает, нужно ли придерживаться совместимых со стандартом ISO правил использования кавычек для разделения идентификаторов и строковых литералов.<br /><br /> 1 = включен;<br /><br /> 0 = выключен.|  
|\<Any other string>|NULL = Введенные значения недопустимы.|  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **sql_variant**  
  
## <a name="remarks"></a>Remarks  
 Параметры SET определяются путем сочетания параметров уровня сервера, уровня базы данных и пользовательских параметров.  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает установку для параметра `CONCAT_NULL_YIELDS_NULL`.  
  
```  
SELECT   SESSIONPROPERTY ('CONCAT_NULL_YIELDS_NULL')  
```  
  
## <a name="see-also"></a>См. также:  
 [sql_variant (Transact-SQL)](../../t-sql/data-types/sql-variant-transact-sql.md)   
 [SET ANSI_NULLS (Transact-SQL)](../../t-sql/statements/set-ansi-nulls-transact-sql.md)   
 [SET ANSI_PADDING (Transact-SQL)](../../t-sql/statements/set-ansi-padding-transact-sql.md)   
 [SET ANSI_WARNINGS (Transact-SQL)](../../t-sql/statements/set-ansi-warnings-transact-sql.md)   
 [SET ARITHABORT (Transact-SQL)](../../t-sql/statements/set-arithabort-transact-sql.md)   
 [SET CONCAT_NULL_YIELDS_NULL (Transact-SQL)](../../t-sql/statements/set-concat-null-yields-null-transact-sql.md)   
 [SET NUMERIC_ROUNDABORT (Transact-SQL)](../../t-sql/statements/set-numeric-roundabort-transact-sql.md)   
 [SET QUOTED_IDENTIFIER (Transact-SQL)](../../t-sql/statements/set-quoted-identifier-transact-sql.md)  
  
  
