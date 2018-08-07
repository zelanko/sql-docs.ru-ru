---
title: Обновление больших объемов данных образец | Документация Майкрософт
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 76ecc05f-a77d-40a2-bab9-91a7fcf17347
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d668b70d2a2591e8df38dd755571147107905c9
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/02/2018
ms.locfileid: "39453418"
---
# <a name="updating-large-data-sample"></a>Образец обновления данных большого объема

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Пример приложения, использующего драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], показывает процесс обновления большого столбца в базе данных.

Файл кода для этого образца имеет имя UpdateLargeData.java и находится в следующей папке:

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\adaptive
```

## <a name="requirements"></a>Требования

Для запуска этого образца приложения также потребуется доступ к образцу базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. Необходимо также включить в параметр classpath путь к файлу sqljdbc4.jar. Если параметр classpath не включает путь к файлу sqljdbc4.jar, то образец приложения вызовет стандартное исключение «Класс не найден». Дополнительные сведения о том, как путь к классу см. в разделе [с помощью драйвера JDBC](../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] содержит файлы библиотек классов sqljdbc.jar, sqljdbc4.jar, sqljdbc41.jar или sqljdbc42.jar, которые используются в зависимости от применяемых параметров среды выполнения Java (JRE). В этом образце используются методы [isWrapperFor](../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md) и [unwrap](../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md), которые были введены в API-интерфейсе JDBC 4.0, для вызова методов буферизации ответов в зависимости от драйвера. Чтобы скомпилировать и выполнить этот образец, понадобится библиотека классов sqljdbc4.jar, которая обеспечивает работу JDBC 4.0. Дополнительные сведения о какие файлы JAR следует выбрать, см. в разделе [требования к системе для драйвера JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

## <a name="example"></a>Пример

В следующем примере образец кода будет использоваться для соединения с базой данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. При помощи образца кода создается объект инструкции и используется метод [isWrapperFor](../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md), чтобы проверить, является ли объект инструкции оболочкой для указанного класса [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md). Метод [unwrap](../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) также используется для получения доступа к методам буферизации ответов в зависимости от драйвера.

Далее при помощи образца кода задается режим буферизации ответов "**adaptive**" при помощи метода [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) класса [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) и демонстрируется установка адаптивного режима буферизации.

Выполняется инструкция SQL, возвращаемые данные размещаются в обновляемый объект [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md).

Наконец, образец кода выполняет проход по строкам данных в результирующем наборе. При обнаружении пустой сводки документа используется комбинация методов [updateString](../../connect/jdbc/reference/updatestring-method-sqlserverresultset.md) и [updateRow](../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) для обновления строки данных и обратного ее сохранения в базе данных. Если данные уже имеются, для отображения некоторых из них используется метод [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md).

По умолчанию в драйвере применяется режим "**adaptive.**" Однако для однопроходных результирующих наборов и в случае, если данные в результирующем наборе превышают по объему доступную память приложения, приложение должно задать адаптивный режим буферизации явным образом, вызвав метод [setResponseBuffering](../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) класса [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md).

[!code[JDBC#UsingAdaptiveBuffering3](../../connect/jdbc/codesnippet/Java/updating-large-data-sample_1.java)]

## <a name="see-also"></a>См. также:

[Работа с большими объемами данных](../../connect/jdbc/working-with-large-data.md)
