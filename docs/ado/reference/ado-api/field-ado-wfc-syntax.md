---
title: Field (ADO-синтаксис WFC) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Field collection [ADO], ADO/WFC syntax
ms.assetid: 7e01cb24-2338-4f92-ad46-8d97248e1a4d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 583e6de7dc8c3ea05d61dda53c3e630d05e4d5f9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918753"
---
# <a name="field-ado---wfc-syntax"></a>Field (ADO — синтаксис WFC)
## <a name="package-commswfcdata"></a>упаковать com. MS. WFC. Data  
  
### <a name="methods"></a>Методы  
  
```  
public void appendChunk(byte[] bytes)  
public void appendChunk(char[] chars)  
public void appendChunk(String chars)  
public byte[] getByteChunk(int len)  
public char[] getCharChunk(int len)  
public String getStringChunk(int len)  
```  
  
### <a name="properties"></a>Свойства  
  
```  
public int getActualSize()  
public int getAttributes()  
public void setAttributes(int pl)  
public com.ms.com.IUnknown getDataFormat()  
public void setDataFormat(com.ms.com.IUnknown format)  
```  
  
 (Дополнительные сведения см. в документации по интерфейсу COM. MS. WFC. Data. Идатаформат.)  
  
```  
public int getDefinedSize()  
public void setDefinedSize(int pl)  
public String getName()  
public int getNumericScale()  
public void setNumericScale(byte pbNumericScale)  
public Variant getOriginalValue()  
public int getPrecision()  
public void setPrecision(byte pbPrecision)  
public int getType()  
public void setType(int pDataType)  
public Variant getUnderlyingValue()  
public Variant getValue()  
public void setValue(Variant value)  
public AdoProperties getProperties()  
```  
  
### <a name="field-accessor-methods"></a>Методы доступа к полям  
 Свойство [value](../../../ado/reference/ado-api/value-property-ado.md) объекта [field](../../../ado/reference/ado-api/field-object.md) Возвращает или задает содержимое этого объекта. Содержимое представляется как вариант, тип объекта, которому можно присвоить значение и любой из нескольких типов данных.  
  
 ADO/WFC реализует свойство **value** с помощью метода **GetValue** , который возвращает объект Variant; и метод **SetValue** , принимающий вариант в качестве аргумента. Варианты в некоторых языках очень эффективны, например в Microsoft Visual Basic.  
  
 В дополнение к свойству **value** , ADO/WFC предоставляет методы *доступа* , которые используют типы данных Java для получения и задания содержимого объектов **field** . Большинство этих методов имеют имена в форме **получить**_DataType_ или **задать**_DataType_.  
  
 Существует два значимых исключения: один из методов **GetObject** возвращает объект, приведенный к указанному классу. Отсутствует свойство **со значением NULL** ; Вместо этого существует свойство **isNull** , возвращающее логическое значение, указывающее, имеет ли поле значение null.  
  
```  
public native boolean getBoolean();  
public void setBoolean(boolean v)  
public native byte getByte();  
public void setByte(byte v)  
public native byte[] getBytes();  
public void setBytes(byte[] v)  
public native double getDouble();  
public void setDouble(double v)  
public native float getFloat();  
public void setFloat(float v)  
public native int getInt();  
public void setInt(int v)  
public native long getLong();  
public void setLong(long v)  
public native short getShort();  
public void setShort(short v)  
public native String getString();  
public void setString(String v)  
public native boolean isNull();  
public void setNull()  
public Object getObject()  
public Object getObject(Class c)  
public void setObject(Object value)  
```  
  
## <a name="see-also"></a>См. также:  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)
