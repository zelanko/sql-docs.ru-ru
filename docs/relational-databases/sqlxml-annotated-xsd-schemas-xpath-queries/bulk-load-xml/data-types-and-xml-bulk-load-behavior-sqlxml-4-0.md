---
title: Типы данных и поведение при выполнении групповой загрузки XML (SQLXML)
description: Сведения о типах данных и работе с массовым загрузкой XML в SQLXML 4,0.
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], data types
- data types [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], data types
ms.assetid: d1ac1939-1f6c-4398-b7a7-a79ca608a4f1
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4e247ae58867054a1051f58f8a17d0d1ef701b2e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85790671"
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a>Типы данных и массовая загрузка XML (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Типы данных, указанные в схеме сопоставления (тип XSD или XDR и **SQL: DataType**), обычно игнорируются, за исключением следующих случаев.  
  
 В XSD.  
  
-   Если тип имеет **значение DateTime** или **time**, необходимо указать **SQL: DataType** , так как при выполнении XML-загрузки выполняется преобразование данных перед отправкой данных в корпорацию Майкрософт [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
-   При выполнении групповой загрузки в столбец типа **uniqueidentifier** в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , а значение XSD — это идентификатор GUID, включающий фигурные скобки ({и}), необходимо указать **SQL: datatype = "uniqueidentifier"** , чтобы удалить фигурные скобки перед вставкой значения в столбец. Если **SQL: DataType** не указан, значение отправляется с фигурными скобками, а вставка завершается ошибкой.  
  
 Дополнительные сведения о **SQL: DataType**см. [в разделе приведение типов данных и Аннотация sql: DATATYPE &#40;&#41;SQLXML 4,0 ](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 В XDR:  
  
-   Если значение **DT: Type** равно **DateTime**, **time**, **DateTime.TZ**или **time.TZ**, необходимо указать оба типа данных **DT: Type** и **SQL: DataType** , так как при выполнении XML-загрузки выполняется преобразование данных перед их отправкой [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
-   Если XML-данные имеют тип **UUID**, необходимо указать **SQL: DataType** . **DT: Type = "UUID"** также требуется, если только данные не являются строковыми данными. Если не указать значение **DT: UUID**, при выполнении XML-загрузки с использованием фигурных скобок будут удалены строки (при необходимости удаляются).  
  
-   Если XML-данные имеют значение **bin. base64** или **bin. hex**, необходимо указать тип данных XML с помощью **DT: Type**. В таком случае при массовой загрузке XML данные загружаются в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в шестнадцатеричном представлении.  
  
  
