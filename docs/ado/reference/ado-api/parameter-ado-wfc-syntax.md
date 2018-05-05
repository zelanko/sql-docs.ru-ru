---
title: Параметр (ADO - синтаксис WFC) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Parameter collection [ADO], ADO/WFC syntax
ms.assetid: d00d1e1e-14b1-41a2-a00f-2a3cb7396f15
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ed007c9dfea10578a642fbb01469eeb6ad2a56da
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="parameter-ado---wfc-syntax"></a>Параметр (ADO - WFC синтаксис)
## <a name="package-commswfcdata"></a>пакет com.ms.wfc.data  
  
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
  
## <a name="parameter-accessor-methods"></a>Параметр метода доступа  
 [Значение](../../../ado/reference/ado-api/value-property-ado.md) свойство [параметр](../../../ado/reference/ado-api/parameter-object.md) объект возвращает или задает содержимое этого объекта. Содержимое представляется как значение типа VARIANT, тип объекта, который может быть присвоено значение и любой из нескольких типов данных.  
  
 Реализует ADO/WFC **значение** свойство с **getValue** метод, возвращающий объект VARIANT; и **setValue** метод, который принимает в качестве аргумента типа VARIANT. Варианты высокоэффективные на некоторых языках, таких как Microsoft Visual Basic.  
  
 В дополнение к **значение** предоставляет свойство, ADO и WFC *доступа* методы, использующие типы данных Java для получения и установки содержимого **параметр** объектов. Большинство из этих методов имеют имена вида **получить *** DataType* или **задать *** DataType*.  
  
 Есть одно исключение внимания: отсутствует не **getNull** свойства; вместо этого используется **isNull** свойство, которое возвращает значение типа Boolean, указывающее, является ли поле значение null.  
  
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
