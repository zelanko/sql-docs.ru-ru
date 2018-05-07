---
title: Функции поддержки различных языков драйвера JDBC | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: bbb74a1d-9278-401f-9530-7b5f45aa79de
caps.latest.revision: 40
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1fd4eb01d7ab8aa2314dfb8f45e0bd08c3b49488
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="international-features-of-the-jdbc-driver"></a>Функции поддержки различных языков драйвера JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Функции интернационализации [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] включают следующее:  
  
-   Поддержка полной локализации на тех же языках, как [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]  
  
-   Поддержка преобразований языка Java для зависящих от языкового стандарта [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] данных  
  
-   Поддержка международных языков независимо от операционной системы.  
  
-   Поддержка международных доменных имен (начиная с Microsoft JDBC Driver 6.0 для SQL Server).  
  
## <a name="handling-of-character-data"></a>Обработка символьных данных  
 Символьные данные на Java обрабатывается в кодировке Юникод, по умолчанию; Java **строка** представляет символьные данные в Юникоде. Единственное исключение из этого правила в драйвере JDBC — методы считывания и задания ASCII-потока, но это особый случай, поскольку в этих методах при обработке байтовых потоков неявно предполагается использование конкретной известной кодовой страницы (ASCII).  
  
 Кроме того, драйвер JDBC предоставляет **sendStringParametersAsUnicode** свойство строки соединения. С помощью этого свойства можно указывать, что подготовленные параметры для символьных данных были отправлены в формате ASCII или MBCS, а не в Юникоде. Дополнительные сведения о **sendStringParametersAsUnicode** свойство строки подключения, в разделе [задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).  
  
### <a name="driver-incoming-conversions"></a>Входящие преобразования драйвера  
 Текстовые данные в Юникоде, приходящие с сервера, преобразовывать не нужно. Они передаются непосредственно в Юникоде. Данные в других форматах, приходящие с сервера, преобразовываются в Юникод из кодировки для данных на уровне базы данных или столбца. Драйвер JDBC использует для выполнения этих преобразований подпрограммы Java Virtual Machine (JVM). Этим преобразованиям подвергаются все методы получения потоков строчных и символьных данных.  
  
 Если база данных не поддерживает нужные кодировки для JVM, то драйвер JDBC вызовет исключение «Кодовая страница ХХХ не поддерживает средой Java». Чтобы решить эту проблему, следует установить полную поддержку международных символов, необходимую для данной виртуальной машины JVM. Пример приведен в документации по поддерживаемым кодировкам на веб-сайте Sun Microsystems.  
  
### <a name="driver-outgoing-conversions"></a>Исходящие преобразования драйвера  
 Символьные данные, исходящие из драйвера на сервер, могут иметь форматы ASCII или Юникод. Например, новые методы JDBC 4.0 национальных символов, таких как методы setNString, setNCharacterStream и setNClob [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) и [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) классов всегда отправьте значения своих параметров на сервер в Юникоде.  
  
 С другой стороны, методы API ненациональных символов, таких как методы setString, setCharacterStream и setClob [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) и [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) классы отправлять их значения на сервер в формате Юникод только если **sendStringParametersAsUnicode** задано значение «true», это значение по умолчанию.  
  
## <a name="non-unicode-parameters"></a>Параметры для кодировок, отличных от Юникода  
 Для достижения оптимальной производительности **CHAR**, **VARCHAR** или **LONGVARCHAR** ввода параметров, отличных от Юникода, задайте **sendStringParametersAsUnicode** подключения строковое свойство, значение «false» и воспользуйтесь методами ненациональных символов.  
  
## <a name="formatting-issues"></a>Особенности форматирования  
 Для даты, времени и валют все форматирование локализованных данных выполняется на уровне языка Java, используя объект языкового стандарта; и различных методов форматирования для **даты**, **календаря**, и **номер** типов данных. В редких случаях, когда драйвер JDBC должен передать зависящие от локали конфиденциальные данные в локализованном формате, нужный инструмент форматирования используется с локалем JVM, заданным по умолчанию.  
  
## <a name="collation-support"></a>Поддержка параметров сортировки  
 Драйвер JDBC Driver 3.0 поддерживает все параметры сортировки, поддерживаемые [!INCLUDE[ssVersion2000](../../includes/ssversion2000_md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)]и новые параметры сортировки или новые версии имен параметров сортировки появился в Windows [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
 Дополнительные сведения о параметрах сортировки см. в разделе [Collation and Unicode Support](http://go.microsoft.com/fwlink/?LinkId=131366) и [имя параметров сортировки Windows (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=131367) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] электронной документации.  
  
## <a name="using-international-domain-names-idn"></a>Использование международных доменных имен (IDN)  
 Драйвер JDBC Driver 6.0 для SQL Server поддерживает использование международных доменных имен (IDN) и можно будет преобразовать имя сервера в Юникоде совместимые кодировке ASCII (Punycode) при необходимости во время подключения.  Если международные доменные имена хранятся в системе доменных имен (DNS) в виде строк ASCII в формате Punycode (как указано в RFC 3490), включите преобразование имени сервера в Юникоде, задав для свойства serverNameAsACE значение true.  В противном случае, если служба DNS настроена на использование символов Юникода, задайте для свойства serverNameAsACE значение false (по умолчанию).  Для более старых версий драйвера JDBC можно также преобразовать имя сервера в Punycode с помощью [Java IDN.toASCII](http://docs.oracle.com/javase/8/docs/api/java/net/IDN.html) методы, прежде чем устанавливать это свойство для соединения.  
  
> [!NOTE]  
>  Большинство программ сопоставителя, написанных для платформ, отличных от Windows, основано на интернет-стандартах DSN, поэтому для международных доменных имен чаще всего используется формат Punycode, хотя DNS-сервер под управлением Windows в частной сети можно в индивидуальном порядке настроить на использование символов UTF-8.  Дополнительные сведения см. в разделе [поддержка символов Юникода](https://technet.microsoft.com/library/cc738403(v=ws.10).aspx).  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
