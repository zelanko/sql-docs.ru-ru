---
title: Поля (ADO — синтаксис WFC) | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 709629c6ef42b8ffeb65959ab9491bbe3c178ab3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47613842"
---
# <a name="field-ado---wfc-syntax"></a>Field (ADO — синтаксис WFC)
## <a name="package-commswfcdata"></a>com.ms.wfc.data пакета  
  
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
  
 (Дополнительные сведения см. документацию по интерфейсу com.ms.wfc.data.IDataFormat).  
  
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
  
### <a name="field-accessor-methods"></a>Методы доступа к полю  
 [Значение](../../../ado/reference/ado-api/value-property-ado.md) свойство [поле](../../../ado/reference/ado-api/field-object.md) объект получает или задает содержимое этого объекта. Содержимое представляется как значение типа VARIANT, тип объекта, который может быть присвоено значение и любой из нескольких типов данных.  
  
 Реализует ADO и WFC **значение** свойство с **getValue** метод, который возвращает объект типа VARIANT; и **setValue** метод, который принимает в качестве аргумента типа VARIANT. Варианты высокой эффективны в некоторых языках, таких как Microsoft Visual Basic.  
  
 В дополнение к **значение** предоставляет свойство, ADO и WFC *доступа* методы, которые используют типы данных Java для получения и задания содержание **поле** объектов. Большинство этих методов имеют имена вида **получить *** DataType* или **задать *** DataType*.  
  
 Существует два исключения, заслуживающие внимания: один из **getObject** методы возвращают объект преобразуется в заданный класс. Существует не **getNull** свойства; вместо этого используется **isNull** свойство, которое возвращает логическое значение, указывающее, является ли поле значение null.  
  
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
  
## <a name="see-also"></a>См. также  
 [Объект Field](../../../ado/reference/ado-api/field-object.md)
