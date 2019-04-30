---
title: Параметр (ADO — синтаксис WFC) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Parameter collection [ADO], ADO/WFC syntax
ms.assetid: d00d1e1e-14b1-41a2-a00f-2a3cb7396f15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ad7331fbbfed123da5d7121d83558ba4bbabc912
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63138696"
---
# <a name="parameter-ado---wfc-syntax"></a>Parameter (ADO — синтаксис WFC)
## <a name="package-commswfcdata"></a>com.ms.wfc.data пакета  
  
### <a name="constructor"></a>Конструктор  
  
```  
public Parameter()  
public Parameter(String name)  
public Parameter(String name, int type)  
public Parameter(String name, int type, int dir)  
public Parameter(String name, int type, int dir, int size)  
public Parameter(String name, int type, int dir, int size, Object value)  
```  
  
### <a name="methods"></a>Методы  
  
```  
public void appendChunk(byte[] bytes)  
public void appendChunk(char[] chars)  
public void appendChunk(String chars)  
```  
  
### <a name="properties"></a>Свойства  
  
```  
public int getAttributes()  
public void setAttributes(int attr)  
public int getDirection()  
public void setDirection(int dir)  
public String getName()  
public void setName(String name)  
public int getNumericScale()  
public void setNumericScale(int scale)  
public int getPrecision()  
public void setPrecision(int prec)  
public int getSize()  
public void setSize(int size)  
public int getType()  
public void setType(int type)  
public com.ms.com.Variant getValue()  
public void setValue(Object v)  
public AdoProperties getProperties()  
```  
  
## <a name="parameter-accessor-methods"></a>Параметр методов доступа  
 [Значение](../../../ado/reference/ado-api/value-property-ado.md) свойство [параметр](../../../ado/reference/ado-api/parameter-object.md) объект получает или задает содержимое этого объекта. Содержимое представляется как значение типа VARIANT, тип объекта, который может быть присвоено значение и любой из нескольких типов данных.  
  
 Реализует ADO и WFC **значение** свойство с **getValue** метод, который возвращает объект типа VARIANT; и **setValue** метод, который принимает в качестве аргумента типа VARIANT. Варианты высокой эффективны в некоторых языках, таких как Microsoft Visual Basic.  
  
 В дополнение к **значение** предоставляет свойство, ADO и WFC *доступа* методы, которые используют типы данных Java для получения и задания содержание **параметр** объектов. Большинство этих методов имеют имена вида **получить**_DataType_ или **задать**_DataType_.  
  
 Есть одно исключение заслуживающие внимания: Существует не **getNull** свойства; вместо этого используется **isNull** свойство, которое возвращает логическое значение, указывающее, является ли поле значение null.  
  
```  
public boolean getBoolean()  
public void setBoolean(boolean v)  
public byte getByte()  
public void setByte(byte v)  
public double getDouble()  
public void setDouble(double v)  
public float getFloat()  
public void setFloat(float v)  
public int getInt()  
public void setInt(int v)  
public long getLong()  
public void setLong(long v)  
public short getShort()  
public void setShort(short v)  
public String getString()  
public void setString(String v)  
public boolean isNull()  
public void setNull()  
```  
  
## <a name="see-also"></a>См. также  
 [Объект Parameter](../../../ado/reference/ado-api/parameter-object.md)
