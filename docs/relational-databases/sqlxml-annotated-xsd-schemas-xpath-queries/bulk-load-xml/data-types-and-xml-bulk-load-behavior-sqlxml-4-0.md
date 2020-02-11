---
title: Типы данных и поведение при выполнении групповой загрузки XML (SQLXML)
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
ms.openlocfilehash: 33619d0d3e1ec5d6684e3dc300317b1cc3666e79
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "75246731"
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a>Типы данных и массовая загрузка XML (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Типы данных, указанные в схеме сопоставления (тип XSD или XDR и **SQL: DataType**), обычно игнорируются, за исключением следующих случаев.  
  
 В XSD.  
  
-   Если тип имеет **значение DateTime** или **time**, необходимо указать **SQL: DataType** , так как при выполнении XML-загрузки выполняется преобразование данных перед отправкой [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]данных в корпорацию Майкрософт.  
  
-   При выполнении групповой загрузки в столбец типа **uniqueidentifier** в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , а значение XSD — это идентификатор GUID, включающий фигурные скобки ({и}), необходимо указать **SQL: datatype = "uniqueidentifier"** , чтобы удалить фигурные скобки перед вставкой значения в столбец. Если **SQL: DataType** не указан, значение отправляется с фигурными скобками, а вставка завершается ошибкой.  
  
 Дополнительные сведения о **SQL: DataType**см. [в разделе приведение типов данных и Аннотация sql: DATATYPE &#40;&#41;SQLXML 4,0 ](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 В XDR:  
  
-   Если значение **DT: Type** равно **DateTime**, **time**, **DateTime.TZ**или **time.TZ**, необходимо указать оба типа данных **DT: Type** и **SQL: DataType** , так как при выполнении XML-загрузки выполняется преобразование данных перед их отправкой [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Если XML-данные имеют тип **UUID**, необходимо указать **SQL: DataType** . **DT: Type = "UUID"** также требуется, если только данные не являются строковыми данными. Если не указать значение **DT: UUID**, при выполнении XML-загрузки с использованием фигурных скобок будут удалены строки (при необходимости удаляются).  
  
-   Если XML-данные имеют значение **bin. base64** или **bin. hex**, необходимо указать тип данных XML с помощью **DT: Type**. В таком случае при массовой загрузке XML данные загружаются в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в шестнадцатеричном представлении.  
  
  
