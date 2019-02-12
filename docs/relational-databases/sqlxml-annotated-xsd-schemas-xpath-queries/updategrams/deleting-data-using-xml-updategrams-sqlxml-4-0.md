---
title: Удаление данных с помощью диаграмм обновления XML (SQLXML 4.0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- <after> block
- updategrams [SQLXML], deleting data
- <before> block
- mapping-schema attribute
- record deletions [SQLXML]
ms.assetid: 4fb116d7-7652-474a-a567-cb475a20765c
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7d878a3dde7ae227e3f2d1394440e0b1e2b7bb1f
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56043075"
---
# <a name="deleting-data-using-xml-updategrams-sqlxml-40"></a>Удаление данных с помощью диаграмм обновления XML (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Диаграмма обновления указывает на операцию удаления, когда экземпляр записи появляется в  **\<перед >** блок без соответствующих записей в  **\<после >** блока. В этом случае диаграмма обновления удаляет запись в  **\<перед >** блок из базы данных.  
  
 Формат диаграммы обновления для операции удаления:  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema="SampleSchema.xml"]  >  
   <updg:before>  
       <ElementName />  
      [<ElementName .../>... ]  
   </updg:before>  
    [<updg:after>  
    </updg:after>]  
  </updg:sync>  
</ROOT>  
```  
  
 Можно опустить  **\<после >** тег, если диаграмма обновления выполняет операцию удаления. Если вы не укажете необязательный **схемы сопоставления** атрибут,  **\<ElementName >** указанный в диаграмме обновления, соответствует таблице базы данных, а дочерние элементы или атрибуты соответствуют столбцы в таблице.  
  
 Если элемент, указанный в диаграмме обновления соответствует более одной строки в таблице или не соответствует любой строке, диаграмма обновления возвращает ошибку и отменяет весь  **\<синхронизации >** блока. В каждый момент времени лишь одна запись может быть удалена элементом в диаграмме обновления.  
  
## <a name="examples"></a>Примеры  
 В примерах этого раздела используется сопоставление по умолчанию (то есть в диаграмме обновления схема сопоставления не указана). Дополнительные примеры диаграмм обновления, которые используются схемы сопоставления, см. в разделе [определение схемы с заметками сопоставления в диаграмме обновления &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
 Чтобы создать рабочие образцы, используя следующие примеры, должны соответствовать требованиям, указанным в [требования для запуска примеров SQLXML](../../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-deleting-a-record-by-using-an-updategram"></a>A. Удаление записи с помощью диаграммы обновления  
 Следующие диаграммы обновления удаляют две записи из таблицы HumanResources.Shift.  
  
 В этих примерах диаграмма обновления не указывает схему сопоставления. Поэтому диаграмма обновления использует сопоставление по умолчанию, в котором имя элемента соответствует имени таблицы, а атрибуты и вложенные элементы соответствуют столбцам.  
  
 Первая диаграмма обновления представляет собой атрибутивную и обозначает две смены (Day-Evening и Evening-Night) в  **\<перед >** блока. Так как нет соответствующей записи в  **\<после >** блок, это операция удаления.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
       <HumanResources.Shift ShiftID="4"  
                        Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift ShiftID="5"  
                        Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
  </updg:before>  
  <updg:after>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>Тестирование диаграммы обновления  
  
1.  Полный пример Б («Вставка нескольких записей с помощью диаграммы обновления») в [Вставка данных с помощью диаграмм обновления XML &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
2.  Скопируйте приведенную выше диаграмму обновления в Блокнот и сохраните его как Updategram-RemoveShifts.xml в той же папке, которая была использована для выполнения («Вставка нескольких записей с помощью диаграммы обновления») в [Вставка данных с помощью диаграмм обновления XML &#40;SQLXML 4.0&#41; ](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
3.  Создайте тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs) и воспользуйтесь им для выполнения диаграммы обновления.  
  
     Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML 4.0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
## <a name="see-also"></a>См. также  
 [Вопросы безопасности диаграмм обновления &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
