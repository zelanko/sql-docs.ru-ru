---
title: "Поля (ADO - синтаксис WFC) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 02/15/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords: Field collection [ADO], ADO/WFC syntax
ms.assetid: 7e01cb24-2338-4f92-ad46-8d97248e1a4d
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 42748fb897d2ec6a7ed226f35852b828ddf82f71
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="field-ado---wfc-syntax"></a>Поля (ADO - WFC синтаксис)
## <a name="package-commswfcdata"></a>пакет com.ms.wfc.data  
  
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
  
 (Дополнительные сведения см. в документации для интерфейса com.ms.wfc.data.IDataFormat.)  
  
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
 [Значение](../../../ado/reference/ado-api/value-property-ado.md) свойство [поле](../../../ado/reference/ado-api/field-object.md) объекта Возвращает или задает содержимое этого объекта. Содержимое представляется как значение типа VARIANT, тип объекта, который может быть присвоено значение и любой из нескольких типов данных.  
  
 Реализует ADO/WFC **значение** свойство с **getValue** метод, возвращающий объект VARIANT; и **setValue** метод, который принимает в качестве аргумента типа VARIANT. Варианты высокоэффективные на некоторых языках, таких как Microsoft Visual Basic.  
  
 В дополнение к **значение** предоставляет свойство, ADO и WFC *доступа* методы, использующие типы данных Java для получения и установки содержимого **поле** объектов. Большинство из этих методов имеют имена вида **получить***DataType* или **задать***DataType*.  
  
 Существует два исключения внимания: один из **getObject** методов возвращает объект, который преобразуется в указанном классе. Имеется не **getNull** свойства; вместо этого используется **isNull** свойство, которое возвращает значение типа Boolean, указывающее, является ли поле значение null.  
  
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
