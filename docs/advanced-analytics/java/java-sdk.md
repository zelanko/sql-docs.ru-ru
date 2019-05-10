---
title: Пакет SDK для Java расширение — расширения языка SQL Server
description: Описание расширения Microsoft SDK для Java для Microsoft SQL Server 2019 г.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/23/2019
ms.topic: conceptual
author: nelgson
ms.author: negust
ms.reviewer: dphansen
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c244d67c7f1cd1636fcd2de0b80454c96927b5d7
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65101821"
---
# <a name="microsoft-extensibility-sdk-for-java-for-sql-server"></a>Расширения Microsoft SDK для Java для SQL Server

В SQL Server CTP-версии 2.5 можно реализовать программу на языке Java для SQL Server с помощью расширения Microsoft SDK для Java. Это интерфейс для расширения языка Java, который используется для обмена данными с SQL Server и для выполнения кода Java из SQL Server.

> [!Note]
> Пакет SDK в CTP-версии 2.5 — большой шаг вперед для предыдущих CTP-версий. Все примеры, имеется рабочий должны будут обновляться, чтобы вместо этого используйте пакет SDK.

Скачайте [расширяемости Microsoft SDK для Java для Microsoft SQL Server](http://aka.ms/mssql-java-lang-extension).

## <a name="implementation-requirements"></a>Требования к реализации

Пакет SDK интерфейс определяет ряд требований, которые должны быть выполнены для SQL Server для взаимодействия со средой выполнения Java. Это означает, что вам необходимо выполнить некоторые правила реализации в классе главного. SQL Server можно затем выполнение метода в Java класса и обмена данных с помощью расширения языка Java.

Пример того, как можно использовать пакет SDK, см. в разделе [пример end-to-end](java-first-sample.md).

## <a name="sdk-classes"></a>Классы пакета SDK

Этот пакет SDK состоит из трех классов.

Два абстрактных классов, которые определяют интерфейс расширения Java использует для обмена данными с SQL Server:

- **AbstractSqlServerExtensionExecutor**
- **AbstractSqlServerExtensionDataset**

Третий класс — вспомогательный класс, который содержит реализацию объекта набора данных. Это необязательный класс, в которых будет производиться было проще приступить к работе. Можно использовать собственную реализацию такого класса.

- **PrimitiveDataset**

Ниже приведено сведения и исходный код для каждого класса в расширение языка Java для SQL Server.

## <a name="abstractsqlserverextensionexecutor"></a>AbstractSqlServerExtensionExecutor

Это абстрактный класс, содержащий интерфейс, используемый для выполнения кода Java с помощью расширения языка Java для SQL Server.

Основной класс Java необходимо наследовать от этого класса. Наследование от этого класса, это означает, что отсутствуют определенные методы в класс, который необходимо реализовать в классе.

Наследовать от этого абстрактного класса расширения с именем абстрактного класса в объявлении класса:

```java
public class <MyClass> extends AbstractSqlServerExtensionExecutor {}
```

Как минимум необходимо реализовать метод execute(...) основного класса.

### <a name="method-execute"></a>Выполнение метода

Метод execute — это метод, который вызывается из SQL Server через расширение языка Java, чтобы вызвать код Java из SQL Server. Это следует рассматривать как основной метод которому мы добавляли основной операции, которые вы хотите выполнить из SQL Server.

Для передачи аргументов метода Java из SQL Server, используйте `@param` параметра в sp_execute_external_script. Метод **выполнение** принимает аргументы таким образом.

```java
public AbstractSqlServerExtensionDataset execute(AbstractSqlServerExtensionDataset input, LinkedHashMap<String, Object> params)  {}
```

### <a name="method-init"></a>Метод init

Метод init выполняется после конструктора и перед вызовом метода execute. Все операции, которые необходимо выполнить перед execute(...) можно сделать в этом методе.

```java
public void init(String sessionId, int taskId, int numtask) {}
```

### <a name="abstractsqlserverextensionexecutor-source-code"></a>AbstractSqlServerExtensionExecutor исходного кода

Дополнительные сведения можно найти ниже в исходном коде:

```java
package com.microsoft.sqlserver.javalangextension;

import com.microsoft.sqlserver.javalangextension.AbstractSqlServerExtensionDataset;
import java.lang.UnsupportedOperationException;
import java.util.LinkedHashMap;

/**
 * Abstract class containing interface used by the Java extension
 */
public abstract class AbstractSqlServerExtensionExecutor {
    /* Supported versions of the Java extension */
    public final int SQLSERVER_JAVA_LANG_EXTENSION_V1 = 1;

    /* Members used by the extension to determine application specifics */
    protected int executorExtensionVersion;
    protected String executorInputDatasetClassName;
    protected String executorOutputDatasetClassName;

    public AbstractSqlServerExtensionExecutor() { }

    public void init(String sessionId, int taskId, int numTasks) {
        /* Default implementation of init() is no-op */
    }

    public AbstractSqlServerExtensionDataset execute(AbstractSqlServerExtensionDataset input, LinkedHashMap<String, Object> params) {
        throw new UnsupportedOperationException("AbstractSqlServerExtensionExecutor execute() is not implemented");
    }

    public void cleanup() {
        /* Default implementation of cleanup() is no-op */
    }
}
```

### <a name="abstractsqlserverextensiondataset"></a>AbstractSqlServerExtensionDataset

Абстрактный класс, содержащий интерфейс для обработки входных и выходных данных, используемых расширением Java.

```java
package com.microsoft.sqlserver.javalangextension;

import java.lang.UnsupportedOperationException;

/**
 * Abstract class containing interface for handling input and output data used by the Java
 * extension.
 */
public class AbstractSqlServerExtensionDataset {
    /**
     * Column metadata interfaces
     */
    public void addColumnMetadata(int columnId, String columnName, int columnType, int precision, int scale) {
        throw new UnsupportedOperationException("addColumnMetadata is not implemented");
    }

    public int getColumnCount() {
        throw new UnsupportedOperationException("getColumnCount is not implemented");
    }

    public String getColumnName(int columnId) {
        throw new UnsupportedOperationException("getColumnName is not implemented");
    }

    public int getColumnPrecision(int columnId) {
        throw new UnsupportedOperationException("getColumnPrecision is not implemented");
    }

    public int getColumnScale(int columnId) {
        throw new UnsupportedOperationException("getColumnScale is not implemented");
    }

    public int getColumnType(int columnId) {
        throw new UnsupportedOperationException("getColumnNullMap is not implemented");
    }

    public boolean[] getColumnNullMap(int columnId) {
        throw new UnsupportedOperationException("getColumnNullMap is not implemented");
    }

    /**
     * Adding column interfaces
     */
    public void addIntColumn(int columnId, int[] rows, boolean[] nullMap) {
        throw new UnsupportedOperationException("addIntColumn is not implemented");
    }

    public void addBooleanColumn(int columnId, boolean[] rows, boolean[] nullMap) {
        throw new UnsupportedOperationException("addBooleanColumn is not implemented");
    }

    public void addLongColumn(int columnId, long[] rows, boolean[] nullMap) {
        throw new UnsupportedOperationException("addLongColumn is not implemented");
    }

    public void addFloatColumn(int columnId, float[] rows, boolean[] nullMap) {
        throw new UnsupportedOperationException("addFloatColumn is not implemented");
    }

    public void addDoubleColumn(int columnId, double[] rows, boolean[] nullMap) {
        throw new UnsupportedOperationException("addDoubleColumn is not implemented");
    }

    public void addShortColumn(int columnId, short[] rows, boolean[] nullMap) {
        throw new UnsupportedOperationException("addShortColumn is not implemented");
    }

    public void addStringColumn(int columnId, String[] rows) {
        throw new UnsupportedOperationException("addStringColumn is not implemented");
    }

    public void addBinaryColumn(int columnId, byte[][] rows) {
        throw new UnsupportedOperationException("addBinaryColumn is not implemented");
    }

    /**
     * Retrieving column interfaces
     */
    public int[] getIntColumn(int columnId) {
        throw new UnsupportedOperationException("getIntColumn is not implemented");
    }

    public long[] getLongColumn(int columnId) {
        throw new UnsupportedOperationException("getLongColumn is not implemented");
    }

    public float[] getFloatColumn(int columnId) {
        throw new UnsupportedOperationException("getFloatColumn is not implemented");
    }

    public short[] getShortColumn(int columnId) {
        throw new UnsupportedOperationException("getShortColumn is not implemented");
    }

    public boolean[] getBooleanColumn(int columnId) {
        throw new UnsupportedOperationException("getBooleanColumn is not implemented");
    }

    public double[] getDoubleColumn(int columnId) {
        throw new UnsupportedOperationException("getDoubleColumn is not implemented");
    }

    public String[] getStringColumn(int columnId) {
        throw new UnsupportedOperationException("getStringColumn is not implemented");
    }

    public byte[][] getBinaryColumn(int columnId) {
        throw new UnsupportedOperationException("getBinaryColumn is not implemented");
    }
}
```

### <a name="primitivedataset"></a>PrimitiveDataset

Этот класс представляет собой реализацию **AbstractSqlServerExtensionDataset** простых типов, хранятся как массивы примитивов. Она предоставляется в пакете SDK просто как вспомогательный класс, который является необязательным для использования.

Если вы не используете этот класс, необходимо реализовать собственный класс, наследующий от **AbstractSqlServerExtensionDataset**.  

```java
package com.microsoft.sqlserver.javalangextension;

import com.microsoft.sqlserver.javalangextension.AbstractSqlServerExtensionDataset;
import java.lang.IllegalArgumentException;
import java.util.HashMap;
import java.util.Map;
import java.util.Map.Entry;

/**
 * Implementation of AbstractSqlServerExtensionDataset that stores
 * simple types as primitives arrays
 */
public class PrimitiveDataset extends AbstractSqlServerExtensionDataset {
    Map<Integer, String>  columnNames;
    Map<Integer, Integer> columnTypes;
    Map<Integer, Integer> columnPrecisions;
    Map<Integer, Integer> columnScales;
    Map<Integer, Object>  columns;
    Map<Integer, boolean[]> columnNullMaps;

    public PrimitiveDataset() {
        columnTypes = new HashMap<>();
        columnNames = new HashMap<>();
        columnPrecisions = new HashMap<>();
        columnScales = new HashMap<>();
        columns = new HashMap<>();
        columnNullMaps = new HashMap<>();
    }

    /**
     * Column metadata interfaces. Metadata is stored in a hash map, using the column ID as the key
     */
    public void addColumnMetadata(int columnId, String columnName, int sqlType, int precision, int scale) {
        if (columnTypes.containsKey(columnId))
        {
            throw new IllegalArgumentException("Metadata for column ID #: " + columnId + " already exists");
        }

        columnTypes.put(columnId, sqlType);
        columnNames.put(columnId, columnName);
        columnPrecisions.put(columnId, precision);
        columnScales.put(columnId, scale);
    }

    public int getColumnCount() {
        return columnTypes.size();
    }

    public String getColumnName(int columnId) {
        checkColumnMetadata(columnId);
        return columnNames.get(columnId);
    }

    public int getColumnPrecision(int columnId) {
        checkColumnMetadata(columnId);
        return columnPrecisions.get(columnId).intValue();
    }

    public int getColumnScale(int columnId) {
        checkColumnMetadata(columnId);
        return columnScales.get(columnId).intValue();
    }

    public int getColumnType(int columnId) {
        checkColumnMetadata(columnId);
        return columnTypes.get(columnId).intValue();
    }

    public boolean[] getColumnNullMap(int columnId) {
        checkColumnMetadata(columnId);
        return columnNullMaps.get(columnId);
    }

    /**
     * Adding column data interfaces. Column data is stored in a hash map, using the column ID as the key and
     * an array of the corresponding type representing each row. Primitives cannot be null, thus null values
     * are represented by an additional boolean array containing a flag to indicate if that value is null.
     * A null indicator array indicates that there are no null values in that column.
     */
    public void addIntColumn(int columnId, int[] rows, boolean[] nullMap) {
        checkColumnMetadata(columnId);
        columns.put(columnId, rows);
        columnNullMaps.put(columnId, nullMap);
    }

    public void addBooleanColumn(int columnId, boolean[] rows, boolean[] nullMap) {
        checkColumnMetadata(columnId);
        columns.put(columnId, rows);
        columnNullMaps.put(columnId, nullMap);
    };

    public void addLongColumn(int columnId, long[] rows, boolean[] nullMap) {
        checkColumnMetadata(columnId);
        columns.put(columnId, rows);
        columnNullMaps.put(columnId, nullMap);
    }

    public void addFloatColumn(int columnId, float[] rows, boolean[] nullMap) {
        checkColumnMetadata(columnId);
        columns.put(columnId, rows);
        columnNullMaps.put(columnId, nullMap);
    }

    public void addDoubleColumn(int columnId, double[] rows, boolean[] nullMap) {
        checkColumnMetadata(columnId);
        columns.put(columnId, rows);
        columnNullMaps.put(columnId, nullMap);
    }

    public void addShortColumn(int columnId, short[] rows, boolean[] nullMap) {
        checkColumnMetadata(columnId);
        columns.put(columnId, rows);
        columnNullMaps.put(columnId, nullMap);
    }

    public void addStringColumn(int columnId, String[] rows) {
        checkColumnMetadata(columnId);
        columns.put(columnId, rows);
    }

    public void addBinaryColumn(int columnId, byte[][] rows) {
        checkColumnMetadata(columnId);
        columns.put(columnId, rows);
    }

    /**
     * Retreiving column data interfaces. For primitive types, calling getColumnNullMap() for the column ID
     * will return the boolean array indicating null values.
     */
    public int[] getIntColumn(int columnId) {
        checkColumnMetadata(columnId);
        return (int[])columns.get(columnId);
    }

    public long[] getLongColumn(int columnId) {
        checkColumnMetadata(columnId);
        return (long[])columns.get(columnId);
    }

    public float[] getFloatColumn(int columnId) {
        checkColumnMetadata(columnId);
        return (float[])columns.get(columnId);
    }

    public short[] getShortColumn(int columnId) {
        checkColumnMetadata(columnId);
        return (short[])columns.get(columnId);
    }

    public boolean[] getBooleanColumn(int columnId) {
        checkColumnMetadata(columnId);
        return (boolean[])columns.get(columnId);
    }

    public double[] getDoubleColumn(int columnId) {
        checkColumnMetadata(columnId);
        return (double[])columns.get(columnId);
    }

    public String[] getStringColumn(int columnId) {
        checkColumnMetadata(columnId);
        return (String[])columns.get(columnId);
    }

    public byte[][] getBinaryColumn(int columnId) {
        checkColumnMetadata(columnId);
        return (byte[][])columns.get(columnId);
    }

    private void checkColumnMetadata(int columnId)
    {
        if (!columnTypes.containsKey(columnId)) {
            throw new IllegalArgumentException("Metadata for column ID #: " + columnId + " does not exist");
        }
    }
}
```

## <a name="next-steps"></a>Следующие шаги

+ [Сквозной пример Java с помощью пакета SDK](java-first-sample.md)
+ [Как вызвать Java в SQL Server](howto-call-java-from-sql.md)
+ [Расширения Java в SQL Server](extension-java.md)
+ [Типы данных Java и SQL Server](java-sql-datatypes.md)
