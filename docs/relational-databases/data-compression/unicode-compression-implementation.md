---
title: "Реализация сжатия Юникода | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-data-compression
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Unicode data compression
- compression [SQL Server], Unicode data
ms.assetid: 44e69e60-9b35-43fe-b9c7-8cf34eaea62a
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 27117e609effaa3ded124a33d742ac9a0b374d6f
ms.lasthandoff: 04/11/2017

---
# <a name="unicode-compression-implementation"></a>Реализация сжатия Юникода
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует алгоритм стандартной схемы сжатия Юникода (SCSU), при этом сохраняются данные в сжатых объектах строк или страниц. Для этих объектов сжатие Юникода для столбцов типов **nchar(n)** и **nvarchar(n)** выполняется автоматически. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] хранит данные Юникода как 2 байта, независимо от локали. Такая кодировка называется UCS-2. Для некоторых локалей реализация сжатия по алгоритму SCSU в SQL Server может сэкономить до 50 % места в хранилище.  
  
## <a name="supported-data-types"></a>Поддерживаемые типы данных  
 Сжатие Юникода поддерживает типы данных фиксированной длины **nchar(n)** и **nvarchar(n)** . Внестрочные значения данных и значения, хранящиеся в столбцах **nvarchar(max)** , не сжимаются.  
  
> [!NOTE]  
>  Сжатие Юникода не поддерживается для данных типа **nvarchar(max)** , даже если они хранятся в строке. Однако сжатие страниц может быть полезно для этого типа данных.  
  
## <a name="upgrading-from-earlier-versions-of-sql-server"></a>Обновление с предыдущих версий SQL Server  
 При обновлении базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]все изменения, связанные со сжатием Юникода, не оказывают влияния на объекты базы данных, сжатые или распакованные. После обновления базы данных ситуация с объектами выглядит следующим образом.  
  
-   Если объект не сжат, то никаких изменений не происходит и объект продолжает работать как раньше.  
  
-   Сжатые объекты строк и страниц продолжают работу как раньше. Распакованные данные остаются в распакованной форме до тех пор, пока их значение не будет обновлено.  
  
-   Для новых строк, вставляемых в таблицу, сжатую на уровне строк или страниц, производится сжатие Юникода.  
  
    > [!NOTE]  
    >  Для использования всех преимуществ сжатия Юникода объект необходимо перестроить с использованием сжатия страниц или строк.  
  
## <a name="how-unicode-compression-affects-data-storage"></a>Влияние сжатия Юникода на хранилище данных  
 При создании или перестройке индекса, а также при изменении значения в таблице, сжатой на уровне строк или страниц, соответствующий индекс или значение сохраняется в сжатом виде только в том случае, если его размер в сжатом виде будет меньше текущего. Сжатие Юникода позволяет предотвратить разрастание размера строк в таблице или индексе.  
  
 Объем места в хранилище, сэкономленного благодаря сжатию, зависит от характеристик сжимаемых данных и локали данных. Следующая таблица содержит данные по экономии, достижимой для некоторых локалей.  
  
|Локаль|Процент сжатия|  
|------------|-------------------------|  
|Английский|50%|  
|Немецкий|50%|  
|Hindi|50%|  
|Турецкий|48 %|  
|Вьетнамский|39 %|  
|Японский|15 %|  
  
## <a name="see-also"></a>См. также:  
 [Сжатие данных](../../relational-databases/data-compression/data-compression.md)   
 [sp_estimate_data_compression_savings (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md)   
 [Реализация сжатия страниц](../../relational-databases/data-compression/page-compression-implementation.md)   
 [sys.dm_db_persisted_sku_features (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-persisted-sku-features-transact-sql.md)  
  
  
