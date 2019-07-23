---
title: Пример считывания данных большого объема | Документация Майкрософт
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6c986144-3854-4352-8331-e79eccbefc28
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cc18dbddf98e41957e0b9e47058a0eab2f65fba9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67957181"
---
# <a name="reading-large-data-sample"></a>Образец считывания данных большого объема

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

В этом примере приложения, использующем драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)], показано, как получить из базы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] большое значение одного столбца с помощью метода [getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md).

Файл кода для этого образца имеет имя ReadLargeData.java и находится в следующей папке:

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\adaptive
```

## <a name="requirements"></a>Требования

Для запуска этого образца приложения также потребуется доступ к образцу базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Кроме того, включите в параметр classpath путь к файлу mssql-jdbc.jar. Дополнительные сведения о настройке подкаталогов классов см. в разделе [Использование драйвера JDBC](../../../connect/jdbc/using-the-jdbc-driver.md).

> [!NOTE]  
> Драйвер [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] включает файлы библиотек классов mssql-jdbc, которые используются в зависимости от выбранных параметров среды выполнения Java (JRE). Для получения дополнительных сведений о том, какой JAR-файл выбрать, см. статью [Требования к системе для драйвера JDBC](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).

## <a name="example"></a>Пример

В следующем примере образец кода будет использоваться для соединения с базой данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]. Затем образец кода создает образцы данных и обновляет таблицу Production.Document с помощью параметризированного запроса.

Кроме того, в образце кода показано, как получить режим адаптивной буферизации с помощью метода [getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md) класса [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md). Обратите внимание, что, начиная с версии драйвера JDBC 2.0, свойство соединения responseBuffering по умолчанию имеет значение «adaptive».

Затем в образце кода выполняется инструкция SQL с объектом [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md), а возвращенные ею данные помещаются в объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).

Наконец, выполняется проход по строкам данных, содержащимся в результирующем наборе, и выполняется доступ к некоторым из этих данных с помощью метода [getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md).

[!code[JDBC#UsingAdaptiveBuffering1](../../../connect/jdbc/codesnippet/Java/reading-large-data-sample_1.java)]

## <a name="see-also"></a>См. также:

[Работа с большими объемами данных](../../../connect/jdbc/code-samples/working-with-large-data.md)
