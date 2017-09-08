---
title: "Тип данных Rowset (XML для Аналитики) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Rowset Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Rowset
- http://schemas.microsoft.com/analysisservices/2003/engine#Rowset
- Rowset
helpviewer_keywords:
- Rowset data type
ms.assetid: a3e6e227-2d53-4530-b369-afa8b4df0a40
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 352dc0e626e3214b37f5047957f8fa1f68aace55
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="rowset-data-type-xmla"></a>Тип данных Rowset (XML для аналитики)
  Определяет производный тип данных, представляющий [корневой](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) элемент, который возвращает табличные данные из [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) или [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) вызова метода.  
  
 **Пространство имен** urn: schemas-microsoft-com: XML-analysis: rowset  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <!-- The following elements extend Resultset -->  
   <!-- Optional schema elements -->  
   <row>...</row>  
</root>  
```  
  
## <a name="data-type-characteristics"></a>Характеристики типа данных  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Базовые типы данных|[Результирующий набор](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|  
|Производные типы данных|None|  
  
## <a name="data-type-relationships"></a>Связи типа данных  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|None|  
|Дочерние элементы|[строки](../../../analysis-services/xmla/xml-elements-properties/row-element-xmla.md)|  
|Производные элементы|[корень](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
  
## <a name="remarks"></a>Замечания  
 В XML нельзя использовать определенные символы в качестве имен элементов и атрибутов. Чтобы устранить это ограничение по именованию, XML для аналитики (XMLA) поддерживает кодировку в соответствии с определением [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Для имен столбцов, содержащих XML-символы, недопустимые в соответствии со спецификацией XML 1.0 XML для Аналитики использует соответствующие шестнадцатеричные значения для преобразования символов Юникода, которые являются недопустимыми. Шестнадцатеричные значения экранируются как _x*HHHH*\_, где *HHHH* означает четырехзначный шестнадцатеричный код UCS-2 для символа в первый заказ старший значащий бит. Например, в XML для аналитики имя «Order Details» будет закодировано как Order_x0020_Details, где символ пробела заменен на соответствующий шестнадцатеричный код.  
  
 Кодирование может усложнить XSL-преобразования. Для поддержки уточняющих запросов для действительных незакодированных имен столбцов, добавьте **SQL: field**атрибут схемы набора строк XML для каждого столбца, как показано в следующем примере:  
  
```  
<xsd:element name="Order_x0020_Details" type="string" sql:field="Order Details" />  
```  
  
> [!NOTE]  
>  **SQL: field** атрибут находится в `"urn:schemas-microsoft-com:xml-sql"` пространства имен.  
  
## <a name="expressing-a-null-value"></a>Указание значения NULL  
 Есть два следующих способа указать значение NULL для столбца внутри строки.  
  
-   При отсутствии элемента столбца подразумевается, что значением столбца является NULL.  
  
-   В элементе столбца может использоваться атрибут `xsi:nil='true'` , указывающий, что столбец имеет значение NULL.  
  
 Например, в строке есть один столбец с именем Store_Name, который имеет значение NULL. Значение столбца Store_Name можно представить в виде отсутствующего элемента столбца: или значение столбца Store_Name можно представить с помощью `xsi:nil='true'` атрибута:  
  
```  
<row>  
   <Store_name xsi:nil='true'/>  
</row>  
```  
  
## <a name="example"></a>Пример  
  
## <a name="xmla-rowset-for-flat-data"></a>Набор строк XMLA для плоских данных  
 Для плоских данных имена столбцов, зависящие от запроса, определяются в схеме в виде имен элементов. Кроме того, каждая строка помещается в пару тегов `<row>`.  
  
 В следующем примере показан формат набора строк XMLA для плоских данных.  
  
```  
<return>  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   </xsd:element>  
      <xsd:complexType name="row">  
         <xsd:choice maxOccurs="unbounded" minOccurs="0">  
            <xsd:element name="CATALOG_NAME" type="xsd:string" sql:field="CATALOG_NAME"></xsd:element>  
            <xsd:element name="DESCRIPTION" type="xsd:string" sql:field="DESCRIPTION"></xsd:element>  
            <xsd:element name="ROLES" type="xsd:string" sql:field="ROLES"></xsd:element>  
            <xsd:element name="DATE_MODIFIED" type="xsd:time" sql:field="DATE_MODIFIED"></xsd:element>  
         </xsd:choice>  
      </xsd:complexType>  
   </xsd:schema>  
   <row>  
      <CATALOG_NAME>FoodMart 2000</CATALOG_NAME>  
      <DESCRIPTION></DESCRIPTION>  
      <ROLES>All Users</ROLES>  
      <DATE_MODIFIED>3/11/2001 6:49:36 PM</DATE_MODIFIED>  
   </row>  
   ...  
</root>  
```  
  
## <a name="xmla-rowset-for-hierarchical-data"></a>Набор строк XMLA для иерархических данных  
 Некоторые наборы строк содержат иерархические данные (или вложенные наборы строк). Наборы строк, возвращаемые запросами интеллектуального анализа данных, являются иерархическими. Для иерархических данных структура строк не меняется, но в схеме, зависящей от данных, определяется подтип элемента, содержащего вложенные данные.  
  
 В следующем примере показан формат набора строк XMLA для иерархических данных. В этом примере подтип элемента, содержащего вложенные данные, равен `<NODE_DISTRIBUTION>`.  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
   xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <xsd:complexType name="row">  
         <xsd:choice maxOccurs="unbounded" minOccurs="0">  
            <xsd:sequence maxOccurs="unbounded" minOccurs="0">  
               <xsd:element name="NODE_DISTRIBUTION" sql:field="NODE_DISTRIBUTION">  
                  <xsd:complexType>  
                     <xsd:choice maxOccurs="unbounded" minOccurs="0">  
                        <xsd:element name="ATTRIBUTE_NAME" type="xsd:string" sql:field="ATTRIBUTE_NAME"></xsd:element>  
                        <xsd:element name="ATTRIBUTE_VALUE" type="xsd:string" sql:field="ATTRIBUTE_VALUE"></xsd:element>  
                        <xsd:element name="SUPPORT" type="xsd:double" sql:field="SUPPORT"></xsd:element>  
                        <xsd:element name="PROBABILITY" type="xsd:double" sql:field="PROBABILITY"></xsd:element>  
                        <xsd:element name="VARIANCE" type="xsd:double" sql:field="VARIANCE"></xsd:element>  
                        <xsd:element name="VALUETYPE" type="xsd:int" sql:field="VALUETYPE"></xsd:element>  
                     </xsd:choice>  
                  </xsd:complexType>  
               </xsd:element>  
            </xsd:sequence>  
            <xsd:element name="MODEL_CATALOG" type="xsd:string" sql:field="MODEL_CATALOG"></xsd:element>  
            <xsd:element name="MODEL_SCHEMA" type="xsd:string" sql:field="MODEL_SCHEMA"></xsd:element>  
            <xsd:element name="MODEL_NAME" type="xsd:string" sql:field="MODEL_NAME"></xsd:element>  
            <xsd:element name="ATTRIBUTE_NAME" type="xsd:string" sql:field="ATTRIBUTE_NAME"></xsd:element>  
            <xsd:element name="NODE_NAME" type="xsd:string" sql:field="NODE_NAME"></xsd:element>  
            <xsd:element name="NODE_UNIQUE_NAME" type="xsd:string" sql:field="NODE_UNIQUE_NAME"></xsd:element>  
            <xsd:element name="NODE_TYPE" type="xsd:unsignedInt" sql:field="NODE_TYPE"></xsd:element>  
            <xsd:element name="NODE_GUID" type="xsd:string" sql:field="NODE_GUID"></xsd:element>  
            <xsd:element name="NODE_CAPTION" type="xsd:string" sql:field="NODE_CAPTION"></xsd:element>  
            <xsd:element name="CHILDREN_CARDINALITY" type="xsd:unsignedInt" sql:field="CHILDREN_CARDINALITY"></xsd:element>  
            <xsd:element name="PARENT_UNIQUE_NAME" type="xsd:string" sql:field="PARENT_UNIQUE_NAME"></xsd:element>  
            <xsd:element name="NODE_DESCRIPTION" type="xsd:string" sql:field="NODE_DESCRIPTION"></xsd:element>  
            <xsd:element name="NODE_RULE" type="xsd:string" sql:field="NODE_RULE"></xsd:element>  
            <xsd:element name="MARGINAL_RULE" type="xsd:string" sql:field="MARGINAL_RULE"></xsd:element>  
            <xsd:element name="NODE_PROBABILITY" type="xsd:double" sql:field="NODE_PROBABILITY"></xsd:element>  
            <xsd:element name="MARGINAL_PROBABILITY" type="xsd:double" sql:field="MARGINAL_PROBABILITY"></xsd:element>  
            <xsd:element name="NODE_SUPPORT" sql:type="xsd:double" sql:field="NODE_SUPPORT"></xsd:element>  
            <xsd:element name="MSOLAP_MODEL_COLUMN" sql:type="xsd:string" sql:field="MSOLAP_MODEL_COLUMN"></xsd:element>  
            <xsd:element name="MSOLAP_NODE_SCORE" sql:type="xsd:double" sql:field="MSOLAP_NODE_SCORE"></xsd:element>  
            <xsd:element name="MSOLAP_NODE_SHORT_CAPTION" sql:type="xsd:string" sql:field="MSOLAP_NODE_SHORT_CAPTION"></xsd:element>  
         </xsd:choice>  
      </xsd:complexType>  
   </xsd:schema>  
   <row>  
      <MODEL_CATALOG>FoodMart 2000</MODEL_CATALOG>  
      <MODEL_NAME>customer pattern discovery</MODEL_NAME>  
      <ATTRIBUTE_NAME>Customers.Name.Member Card</ATTRIBUTE_NAME>  
      <NODE_NAME>2147483652</NODE_NAME>  
      <NODE_UNIQUE_NAME>2147483652</NODE_UNIQUE_NAME>  
      <NODE_TYPE>2</NODE_TYPE>  
      <NODE_CAPTION>All</NODE_CAPTION>  
      <CHILDREN_CARDINALITY>8</CHILDREN_CARDINALITY>  
      <PARENT_UNIQUE_NAME>0</PARENT_UNIQUE_NAME>  
      <NODE_DESCRIPTION>All</NODE_DESCRIPTION>  
      <NODE_RULE></NODE_RULE>  
      <MARGINAL_RULE></MARGINAL_RULE>  
      <NODE_PROBABILITY>1</NODE_PROBABILITY>  
      <MARGINAL_PROBABILITY>1</MARGINAL_PROBABILITY>  
      <NODE_DISTRIBUTION>  
         <ATTRIBUTE_NAME>Customers.Name.Member Card</ATTRIBUTE_NAME>  
         <ATTRIBUTE_VALUE>missing</ATTRIBUTE_VALUE>  
         <SUPPORT>0</SUPPORT>  
         <PROBABILITY>0</PROBABILITY>  
         <VARIANCE>0</VARIANCE>  
         <VALUETYPE>1</VALUETYPE></NODE_DISTRIBUTION>  
      <NODE_DISTRIBUTION>  
         <ATTRIBUTE_NAME>Customers.Name.Member Card</ATTRIBUTE_NAME>  
         <ATTRIBUTE_VALUE>Bronze</ATTRIBUTE_VALUE>  
         <SUPPORT>3077</SUPPORT>  
         <PROBABILITY>0.551334886221107</PROBABILITY>  
         <VARIANCE>0</VARIANCE>  
         <VALUETYPE>4</VALUETYPE></NODE_DISTRIBUTION>  
      <NODE_DISTRIBUTION>  
         <ATTRIBUTE_NAME>Customers.Name.Member Card</ATTRIBUTE_NAME>  
         <ATTRIBUTE_VALUE>Golden</ATTRIBUTE_VALUE>  
         <SUPPORT>659</SUPPORT>  
         <PROBABILITY>0.118079197276474</PROBABILITY>  
         <VARIANCE>0</VARIANCE>  
         <VALUETYPE>4</VALUETYPE></NODE_DISTRIBUTION>  
      <NODE_DISTRIBUTION>  
         <ATTRIBUTE_NAME>Customers.Name.Member Card</ATTRIBUTE_NAME>  
         <ATTRIBUTE_VALUE>Normal</ATTRIBUTE_VALUE>  
         <SUPPORT>1332</SUPPORT>  
         <PROBABILITY>0.238666905572478</PROBABILITY>  
         <VARIANCE>0</VARIANCE>  
         <VALUETYPE>4</VALUETYPE></NODE_DISTRIBUTION>  
      <NODE_DISTRIBUTION>  
         <ATTRIBUTE_NAME>Customers.Name.Member Card</ATTRIBUTE_NAME>  
         <ATTRIBUTE_VALUE>Silver</ATTRIBUTE_VALUE>  
         <SUPPORT>513</SUPPORT>  
         <PROBABILITY>9.19190109299409E-02</PROBABILITY>  
         <VARIANCE>0</VARIANCE>  
         <VALUETYPE>4</VALUETYPE></NODE_DISTRIBUTION>  
      <NODE_SUPPORT>5581</NODE_SUPPORT>  
      <MSOLAP_MODEL_COLUMN>Customers.Name.Member Card</MSOLAP_MODEL_COLUMN>  
      <MSOLAP_NODE_SCORE>1948.401692055</MSOLAP_NODE_SCORE>  
      <MSOLAP_NODE_SHORT_CAPTION>All</MSOLAP_NODE_SHORT_CAPTION>  
</row>  
</root>  
```  
  
## <a name="see-also"></a>См. также:  
 [Типы данных XML &#40; XML для Аналитики &#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)  
  
  
