---
title: NEWSEQUENTIALID (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 08/08/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- NEWSEQUENTIALID
- NEWSEQUENTIALID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- NEWSEQUENTIALID function
- GUIDs [SQL Server]
ms.assetid: e06d2cab-f1ff-42f1-8550-6aaec57be36f
caps.latest.revision: 33
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1a1c5e86197ec543fcf34f2303889cc66d756f07
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/04/2018
ms.locfileid: "37790165"
---
# <a name="newsequentialid-transact-sql"></a>NEWSEQUENTIALID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Создает идентификатор GUID, имеющий значение, большее любого идентификатора GUID, который был прежде создан на указанном компьютере при помощи этой функции с момента запуска Windows. После перезагрузки Windows идентификатор GUID может вновь начинаться с более низкого диапазона, однако останется глобально уникальным. Если столбец GUID используется в качестве идентификатора строки, использование NEWSEQUENTIALID может ускорить работу по сравнению с использованием функции NEWID, поскольку функция NEWID вызывает непредсказуемый уровень нагрузки и использует меньшее число кэшированных страниц данных. Использование NEWSEQUENTIALID также помогает полностью заполнять страницы данных и страницы индекса.  
  
> [!IMPORTANT]  
>  Если важна конфиденциальность, то не следует применять эту функцию. Значение следующего формируемого идентификатора GUID можно предугадать и, следовательно, получить доступ к данным, связанным с этим идентификатором GUID.  
  
 NEWSEQUENTIALID является оболочкой для функции Windows [UuidCreateSequential](http://go.microsoft.com/fwlink/?LinkId=164027) с применением [случайной перестановки байт](https://blogs.msdn.microsoft.com/dbrowne/2012/07/03/how-to-generate-sequential-guids-for-sql-server-in-net/).
  
> [!WARNING]  
>  У функции UuidCreateSequential есть аппаратные зависимости. На [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно разработать кластеры последовательных значений при перемещении баз данных (например, автономных баз данных) на другие компьютеры. При использовании AlwaysOn и на [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] кластеры последовательных значений можно разработать при отработке отказа базы данных на другой компьютер.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
NEWSEQUENTIALID ( )  
```  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **uniqueidentifier**  
  
## <a name="remarks"></a>Remarks  
 Функция NEWSEQUENTIALID() может быть использована только для ограничений DEFAULT для столбцов таблицы типа **uniqueidentifier**. Пример:  
  
```  
CREATE TABLE myTable (ColumnA uniqueidentifier DEFAULT NEWSEQUENTIALID());   
```  
  
 Когда функция NEWSEQUENTIALID() используется в выражениях DEFAULT, она не может быть объединена с другими скалярными операторами. Например, нельзя выполнить следующее:  
  
```  
CREATE TABLE myTable (ColumnA uniqueidentifier DEFAULT dbo.myfunction(NEWSEQUENTIALID()));  
```  
  
 В предыдущем примере `myfunction()` является пользовательской скалярной функцией, которая принимает и возвращает значение `uniqueidentifier`.  
  
 На функцию NEWSEQUENTIALID нельзя ссылаться в запросах.  
  
 Функцию NEWSEQUENTIALID можно использовать для формирования идентификаторов GUID, чтобы уменьшить число разбиений страниц и произвольных операций ввода-вывода на конечном уровне индексов.  
  
 Каждый идентификатор GUID, сформированный с помощью функции NEWSEQUENTIALID, является уникальным на данном компьютере. Идентификаторы GUID, сформированные с помощью функции NEWSEQUENTIALID, становятся уникальными для нескольких компьютеров, только если в компьютере-источнике имеется сетевая плата.  
  
## <a name="see-also"></a>См. также:  
 [NEWID (Transact-SQL)](../../t-sql/functions/newid-transact-sql.md)   
 [Операторы сравнения (Transact-SQL)](../../t-sql/language-elements/comparison-operators-transact-sql.md)  
  
  
