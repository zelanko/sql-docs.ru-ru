---
title: Функции поддержки различных языков драйвера JDBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: bbb74a1d-9278-401f-9530-7b5f45aa79de
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 45ad47f53b36a54843aacb985e3d9c3db3d55d01
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2018
ms.locfileid: "52398337"
---
# <a name="international-features-of-the-jdbc-driver"></a>Функции поддержки различных языков драйвера JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Функции интернационализации [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] включают в себя следующее.  
  
-   Поддержка полной локализации на тех же языках, что и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Поддержка преобразований языка Java для данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], зависящих от языкового стандарта.  
  
-   Поддержка международных языков независимо от операционной системы.  
  
-   Поддержка международных доменных имен (начиная с Microsoft JDBC Driver 6.0 для SQL Server).  
  
## <a name="handling-of-character-data"></a>Обработка символьных данных  
 Символьные данные на Java по умолчанию рассматриваются как данные в формате Юникода. Объект Java **String** представляет символьные данные в формате Юникода. Единственное исключение из этого правила в драйвере JDBC — методы считывания и задания ASCII-потока, но это особый случай, поскольку в этих методах при обработке байтовых потоков неявно предполагается использование конкретной известной кодовой страницы (ASCII).  
  
 Кроме того, драйвер JDBC обеспечивает **sendStringParametersAsUnicode** свойство строки подключения. С помощью этого свойства можно указывать, что подготовленные параметры для символьных данных были отправлены в формате ASCII или MBCS, а не в Юникоде. Дополнительные сведения о **sendStringParametersAsUnicode** свойство строки подключения, см. в разделе [заданию свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).  
  
### <a name="driver-incoming-conversions"></a>Входящие преобразования драйвера  
 Текстовые данные в Юникоде, приходящие с сервера, преобразовывать не нужно. Они передаются непосредственно в Юникоде. Данные в других форматах, приходящие с сервера, преобразовываются в Юникод из кодировки для данных на уровне базы данных или столбца. Драйвер JDBC использует для выполнения этих преобразований подпрограммы Java Virtual Machine (JVM). Этим преобразованиям подвергаются все методы получения потоков строчных и символьных данных.  
  
 Если база данных не поддерживает нужные кодировки для JVM, то драйвер JDBC вызовет исключение «Кодовая страница ХХХ не поддерживает средой Java». Чтобы решить эту проблему, следует установить полную поддержку международных символов, необходимую для данной виртуальной машины JVM. Пример приведен в документации по поддерживаемым кодировкам на веб-сайте Sun Microsystems.  
  
### <a name="driver-outgoing-conversions"></a>Исходящие преобразования драйвера  
 Символьные данные, исходящие из драйвера на сервер, могут иметь форматы ASCII или Юникод. Например, новые методы национальных символов в JDBC 4.0, такие как методы setNString, setNCharacterStream и setNClob классов [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) и [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md), всегда выполняют отправку на сервер своих значений параметров в формате Юникода.  
  
 C другой стороны, методы для API ненациональных символов, такие как setString, setCharacterStream и setClob классов [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) и [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md), отправляют на сервер значения своих параметров в формате Юникода, только если свойство **sendStringParametersAsUnicode** имеет значение True (это значение по умолчанию).  
  
## <a name="non-unicode-parameters"></a>Параметры для кодировок, отличных от Юникода  
 Для достижения оптимальной производительности **CHAR**, **VARCHAR** или **LONGVARCHAR** тип параметров не в Юникоде, задайте **sendStringParametersAsUnicode** подключения свойство «false» строки и воспользуйтесь методами ненациональных символов.  
  
## <a name="formatting-issues"></a>Особенности форматирования  
 Все форматирование локализованных данных для дат, времени и валют выполняется на уровне языка Java с помощью объекта Locale и различных методов форматирования для типов данных **Date**, **Calendar** и **Number**. В редких случаях, когда драйвер JDBC должен передать зависящие от локали конфиденциальные данные в локализованном формате, нужный инструмент форматирования используется с локалем JVM, заданным по умолчанию.  
  
## <a name="collation-support"></a>Поддержка параметров сортировки  
 В версии JDBC Driver 3.0 поддерживаются все параметры сортировки, поддерживаемые [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], а также новые параметры сортировки и новые версии имен параметров сортировки Windows, реализованные в [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
 Дополнительные сведения о параметрах сортировки см. в разделах [Поддержка параметров сортировки и Юникода](https://go.microsoft.com/fwlink/?LinkId=131366) и [Имя параметров сортировки Windows (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=131367) электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="using-international-domain-names-idn"></a>Использование международных доменных имен (IDN)  
 JDBC Driver 6.0 для SQL Server поддерживает использование международных доменных имен (IDN), которые при необходимости могут преобразовать имя сервера в Юникоде в кодировку, совместимую с ASCII (Punycode), во время подключения.  Если международные доменные имена хранятся в системе доменных имен (DNS) в виде строк ASCII в формате Punycode (как указано в RFC 3490), включите преобразование имени сервера в Юникоде, задав для свойства serverNameAsACE значение true.  В противном случае, если служба DNS настроена на использование символов Юникода, задайте для свойства serverNameAsACE значение false (по умолчанию).  Для более старых версий JDBC Driver можно также преобразовать имя сервера в Punycode с помощью методов [IDN.toASCII Java](https://docs.oracle.com/javase/8/docs/api/java/net/IDN.html), прежде чем устанавливать это свойство для подключения.  
  
> [!NOTE]  
>  Большинство программ сопоставителя, написанных для платформ, отличных от Windows, основано на интернет-стандартах DSN, поэтому для международных доменных имен чаще всего используется формат Punycode, хотя DNS-сервер под управлением Windows в частной сети можно в индивидуальном порядке настроить на использование символов UTF-8.  Дополнительные сведения см. в разделе [Поддержка символов Юникода](https://technet.microsoft.com/library/cc738403(v=ws.10).aspx).  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
