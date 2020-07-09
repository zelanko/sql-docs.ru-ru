---
title: HOST_NAME (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 09/21/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- HOST_NAME_TSQL
- HOST_NAME
dev_langs:
- TSQL
helpviewer_keywords:
- HOST_NAME function
- workstation names [SQL Server]
ms.assetid: 4b8b0705-c083-4b07-b954-c83ee73b2ebb
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 7bde33153b10b7c708c92150104414d326fb1f0b
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86011666"
---
# <a name="host_name-transact-sql"></a>HOST_NAME (Transact-SQL)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

  Возвращает имя рабочей станции.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HOST_NAME ()  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **nvarchar(128)**  
  
## <a name="remarks"></a>Remarks  
 Если параметр системной функции является необязательным, то предполагаются текущие база данных, главный компьютер, пользователь сервера или пользователь базы данных. За встроенными функциями всегда должны следовать круглые скобки.  
  
 Системные функции можно использовать в списке выбора, в предложении WHERE и в любом месте, где разрешается использование выражений.  
  
> [!IMPORTANT]  
>  Имя рабочей станции предоставляется клиентским приложением, оно может предоставлять неточные данные. Не следует полагаться на функцию HOST_NAME для обеспечения безопасности.  
  
## <a name="examples"></a>Примеры  
 В следующем примере создается таблица, в которой функция `HOST_NAME()` используется в определении `DEFAULT` для записи имен рабочих станций, которые вставляют в таблицу строки при регистрации заказов.  
  
```  
CREATE TABLE Orders  
   (OrderID     int        PRIMARY KEY,  
    CustomerID  nchar(5)   REFERENCES Customers(CustomerID),  
    Workstation nchar(30)  NOT NULL DEFAULT HOST_NAME(),  
    OrderDate   datetime   NOT NULL,  
    ShipDate    datetime   NULL,  
    ShipperID   int        NULL REFERENCES Shippers(ShipperID));  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Выражения (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-category-transact-sql.md)  
  
  
