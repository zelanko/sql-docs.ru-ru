---
title: "Драйвер Microsoft JDBC для SQL Server Support Matrix | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5769e67-99f7-4bc1-a4fa-8941dad33d35
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 35747cff6a18c79a828e5269d7085c710338bf18
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="microsoft-jdbc-driver-for-sql-server-support-matrix"></a>Матрица поддержки драйвера Microsoft JDBC Driver for SQL Server
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  В этой статье приведены матрица и политика жизненного цикла поддержки для драйвера Microsoft JDBC Driver for SQL Server.  
  
## <a name="microsoft-jdbc-driver-support-lifecycle-matrix-and-policy"></a>Матрица и политика жизненного цикла поддержки для драйвера Microsoft JDBC  
 Политика жизненного цикла поддержки Майкрософт (MSL) предоставляет понятную и предсказуемую информацию о жизненном цикле поддержки продуктов Майкрософт. Основная фаза поддержки драйверов JDBC версий 3.0 и 4.x длится пять лет с даты выпуска соответствующей версии. Основная фаза поддержки определена на веб-сайте жизненного цикла поддержки Майкрософт.  
  
 Возможность расширенной или настраиваемой поддержки драйвера JDBC не предусмотрена.  
    
 Перечисленные ниже версии драйверов Microsoft JDBC будут поддерживаться до указанной даты окончания поддержки.  
  
|Имя драйвера|Версия пакета драйверов|Применимые JAR(s)|Конец Основная фаза поддержки|
|-|-|-|-|  
|6.2 драйвер Microsoft JDBC для SQL Server|6.2|MSSQL jdbc-6.2.1.jre8.jar<br> MSSQL jdbc-6.2.1.jre7.jar|30 июня 2022|    
|Microsoft JDBC Driver 6.0 для SQL Server|6.0|sqljdbc42.jar<br>sqljdbc41.jar|14 июля 2021|    
|Microsoft JDBC Driver 4.2 for SQL Server|4.2|sqljdbc42.jar<br>sqljdbc41.jar|24 августа 2020 г.|  
|Microsoft JDBC Driver 4.1 for SQL Server|4.1|sqljdbc41.jar|12 декабря 2019 г.|  
  
 Следующие драйверы Microsoft JDBC больше не поддерживаются.  
 
|Имя драйвера|Версия пакета драйверов|Конец Основная фаза поддержки|  
|-|-|-|
|Microsoft JDBC Driver 4.0 for SQL Server|4.0|6 марта 2017 г.|  
|Драйвер JDBC 3.0 для Microsoft SQL Server|3.0|23 апреля 2015 г.|  
|Драйвер JDBC 2.0 для Microsoft SQL Server|2.0|31 декабря 2012 г.|  
|Драйвер JDBC 1.2 для Microsoft SQL Server 2005|1.2|25 июня 2011 г.|  
|Драйвер JDBC 1.1 для Microsoft SQL Server 2005|1.1|25 июня 2011 г.|  
|Драйвер JDBC 1.0 для Microsoft SQL Server 2005|1.0|25 июня 2011 г.|  
|Драйвер JDBC для Microsoft SQL Server 2000|2000|9 июля 2010 г.|  
  
## <a name="sql-version-compatibility"></a>Совместимость с версиями SQL  
  
|Версия драйвера|SQL Server 2008|SQL Server 2008 R2|SQL Server 2012|База данных SQL Azure|PDW 2008R2 AU3<sup>4</sup>|SQL Server 2014|SQL Server 2016|  
|-|-|-|-|-|-|-|-| 
|6.2|Да|Да|Да|Да|Да|Да|Да|  
|6.1|Да|Да|Да|Да|Да|Да|Да|  
|6.0|Да|Да|Да|Да|Да|Да|Да|  
|4.2|Да|Да|Да|Да|Да|Да|Да|  
|4.1|Да|Да|Да|Да|Да|Да|Да|  
|4.0|Да|Да|Да|Да|Да|Да|Да|  
|3.0|Да|Да|Y<sup>1</sup>|Y<sup>2</sup>|Нет|Y<sup>5</sup>|Нет|  
|2.0|Y<sup>3</sup>|Y<sup>3</sup>|Нет|Нет|Нет|Нет|Нет|  
|1.2|Y<sup>3</sup>|Нет|Нет|Нет|Нет|Нет|Нет|  
|1.1|Нет|Нет|Нет|Нет|Нет|Нет|Нет|  
|1.0|Нет|Нет|Нет|Нет|Нет|Нет|Нет|  
|2000|Нет|Нет|Нет|Нет|Нет|Нет|Нет|  
  
 <sup>1</sup>драйвера JDBC версии 3.0 для Microsoft SQL Server можно подключиться к SQL Server 2012 в качестве клиента нижнего уровня.  
  
 <sup>2</sup>поддержка базы данных SQL Azure появилась в версии 3.0 в исправлении. Мы рекомендуем пользователям баз данных SQL Azure использовать последнюю версию драйвера.  
  
 <sup>3</sup>драйвера JDBC версии 2.0 для Microsoft SQL Server и Microsoft SQL Server 2005 JDBC Driver версии 1.2 можно подключиться к SQL Server 2008 в качестве клиента нижнего уровня. Когда допускается подключение к клиенту более низкого уровня с последующим преобразованием данных, приложения могут выполнять запросы и выполнять обновления для таких новых типов данных SQL Server 2008: time, date, datetime2, datetimeoffset и FILESTREAM. Дополнительные сведения о том, как использовать эти новые типы данных с помощью драйвера JDBC, см. в статьях  [Working with SQL Server 2008 Date/Time Data Types using v1.2 JDBC driver](http://go.microsoft.com/fwlink/?LinkId=145198) (Использование типов данных Date и Time в SQL Server 2008 с помощью драйвера JDBC 1.2) и  [Working with SQL Server 2008 Filestream using v1.2 JDBC driver](http://go.microsoft.com/fwlink/?LinkId=145199)(Использование типа данных Filestream в SQL Server 2008 с помощью драйвера JDBC). Дополнительные сведения об обратной совместимости новых типов данных см. в статьях  [Использование данных даты и времени](http://go.microsoft.com/fwlink/?LinkId=145211)и  [Поддержка FILESTREAM](http://go.microsoft.com/fwlink/?LinkId=145212) в электронной документации по SQL Server.  
  
 <sup>4</sup>поддержка соединений между драйвером Microsoft JDBC и Parallel Data Warehouse введен в Microsoft JDBC Driver 4.0 для SQL Server и Microsoft SQL Server 2008 R2 параллельных данных хранилища устройства обновления 3.  
  
 <sup>5</sup>драйвера JDBC версии 3.0 для Microsoft SQL Server можно подключиться к SQL Server 2014 в качестве клиента нижнего уровня.  
  
## <a name="java-and-jdbc-specification-support"></a>Совместимость версий Java и JDBC  
  
|Версия драйвера JDBC|Версия JRE|Версия API JDBC| 
|-|-|-|  
|6.2|1.7, 1.8|4.1, 4.2|  
|6.1|1.7, 1.8|4.1, 4.2|  
|6.0|1.7, 1.8|4.1, 4.2|  
|4.2|1.7, 1.8|4.1, 4.2|  
|4.1|1.7|4.0|  
|4.0|1.5, 1.6, 1.7|3.0, 4.0|  
|3.0|1.5, 1.6,|3.0, 4.0|  
|2.0|1.5, 1.6|3.0, 4.0|  
|1.2|1.4, 1.5, 1.6|3.0|  
|1.1|1.4|3.0|  
|1.0|1.4|3.0|  
|2000|1.4|3.0|  
  
## <a name="supported-operating-systems"></a>Поддерживаемые операционные системы  
 Драйвер JDBC может работать со всеми операционными системами, поддерживающими виртуальную машину Java (JVM). Вот некоторые из наиболее распространенных систем: Windows 10, Windows 8.1, Windows 8, Windows 7, Windows Server 2008 R2, Windows Vista, Linux, Unix, AIX, MacOS и др.  
  
 Разработчики JDBC тестируют драйвер в операционных системах Windows, Sun Solaris, SUSE Linux и RedHat Linux.  Техническая поддержка доступна для пользователей всех платформ, но мы можем попросить вас воспроизвести проблему на вашей платформе, например в ОС Windows.  
  
## <a name="application-server-support"></a>Поддержка сервера приложений  
 Драйвер Microsoft JDBC Driver for SQL Server тестируется на совместимость с различными серверами приложений.  Обратитесь к поставщику вашего сервера приложений, чтобы узнать, какая версия драйвера совместима с их продуктом.  
  
  

