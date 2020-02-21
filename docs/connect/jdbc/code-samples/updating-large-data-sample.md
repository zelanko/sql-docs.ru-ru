---
title: Пример обновления большого объема данных | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 76ecc05f-a77d-40a2-bab9-91a7fcf17347
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1bd284f6fb8021164aa3edf6aa31761b7483406e
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "69028261"
---
# <a name="updating-large-data-sample"></a>Пример обновления большого объема данных

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

Пример приложения, использующего драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], показывает процесс обновления большого столбца в базе данных.

Файл кода для этого образца имеет имя UpdateLargeData.java и находится в следующей папке:

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\adaptive
```

## <a name="requirements"></a>Требования

Для запуска этого образца приложения также потребуется доступ к образцу базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Также включите в параметр classpath путь к файлу sqljdbc4.jar. Если параметр classpath не включает путь к файлу sqljdbc4.jar, то образец приложения вызовет стандартное исключение «Класс не найден». Дополнительные сведения о том, как настроить параметр classpath, см. в статье [Использование JDBC Driver](../../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> Драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] содержит файлы библиотек классов sqljdbc.jar, sqljdbc4.jar, sqljdbc41.jar или sqljdbc42.jar, которые используются в зависимости от применяемых параметров среды выполнения Java (JRE). В этом образце используются методы [isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md) и [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md), которые были введены в API-интерфейсе JDBC 4.0, для вызова методов буферизации ответов в зависимости от драйвера. Чтобы скомпилировать и выполнить этот образец, понадобится библиотека классов sqljdbc4.jar, которая обеспечивает работу JDBC 4.0. Дополнительные сведения о выборе JAR-файла см. в описании [требований к системе для JDBC Driver](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

## <a name="example"></a>Пример

В следующем примере образец кода будет использоваться для соединения с базой данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. При помощи образца кода создается объект инструкции и используется метод [isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md), чтобы проверить, является ли объект инструкции оболочкой для указанного класса [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md). Метод [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) также используется для получения доступа к методам буферизации ответов в зависимости от драйвера.

Далее при помощи образца кода задается режим буферизации ответов "**adaptive**" при помощи метода [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) класса [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) и демонстрируется установка адаптивного режима буферизации.

Затем выполняется инструкция SQL, возвращаемые данные размещаются в обновляемый объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).

Наконец, образец кода выполняет проход по строкам данных в результирующем наборе. При обнаружении пустой сводки документа используется комбинация методов [updateString](../../../connect/jdbc/reference/updatestring-method-sqlserverresultset.md) и [updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) для обновления строки данных и обратного ее сохранения в базе данных. Если данные уже имеются, для отображения некоторых из них используется метод [getString](../../../connect/jdbc/reference/getstring-method-sqlserverresultset.md).

По умолчанию в драйвере применяется режим "**adaptive.** " Однако для однопроходных результирующих наборов и в случае, если данные в результирующем наборе превышают по объему доступную память приложения, приложение должно задать адаптивный режим буферизации явным образом, вызвав метод [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) класса [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).

[!code[JDBC#UsingAdaptiveBuffering3](../../../connect/jdbc/codesnippet/Java/updating-large-data-sample_1.java)]

## <a name="see-also"></a>См. также раздел

[Работа с большими объемами данных](../../../connect/jdbc/code-samples/working-with-large-data.md)
