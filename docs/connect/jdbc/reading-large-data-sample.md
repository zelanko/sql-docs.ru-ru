---
title: Пример считывания большого объема данных | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6c986144-3854-4352-8331-e79eccbefc28
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 260666488a21b02c0c318d3277b72fc576b0ab08
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "69027823"
---
# <a name="reading-large-data-sample"></a>Пример считывания большого объема данных

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

В этом примере приложения, использующем драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], показано, как получить из базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] большое значение одного столбца с помощью метода [getCharacterStream](../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md).

Файл кода для этого образца имеет имя ReadLargeData.java и находится в следующей папке:

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\adaptive
```

## <a name="requirements"></a>Требования

Для запуска этого образца приложения также потребуется доступ к образцу базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. Необходимо также включить в параметр classpath путь к файлу mssql-jdbc.jar. Дополнительные сведения о том, как настроить параметр classpath, см. в статье [Использование JDBC Driver](../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] включает файлы библиотек классов mssql-jdbc, которые используются в зависимости от выбранных параметров среды выполнения Java (JRE). Для получения дополнительных сведений о том, какой JAR-файл выбрать, см. статью [Требования к системе для драйвера JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

## <a name="example"></a>Пример

В следующем примере образец кода будет использоваться для соединения с базой данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. Затем образец кода создает образцы данных и обновляет таблицу Production.Document с помощью параметризированного запроса.

Кроме того, в образце кода показано, как получить режим адаптивной буферизации с помощью метода [getResponseBuffering](../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md) класса [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md). Обратите внимание, что, начиная с версии драйвера JDBC 2.0, свойство соединения responseBuffering по умолчанию имеет значение «adaptive».

Затем в образце кода выполняется инструкция SQL с объектом [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), а возвращенные ею данные помещаются в объект [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md).

Наконец, выполняется проход по строкам данных, содержащимся в результирующем наборе, и выполняется доступ к некоторым из этих данных с помощью метода [getCharacterStream](../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md).

[!code[JDBC#UsingAdaptiveBuffering1](../../connect/jdbc/codesnippet/Java/reading-large-data-sample_1.java)]

## <a name="see-also"></a>См. также раздел

[Работа с большими объемами данных](../../connect/jdbc/working-with-large-data.md)
