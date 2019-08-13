---
title: Матрица поддержки Microsoft JDBC Driver для SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 08/01/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c5769e67-99f7-4bc1-a4fa-8941dad33d35
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 04d7fe419c8639d9f14c3c3795a1007d947c3998
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68893253"
---
# <a name="microsoft-jdbc-driver-for-sql-server-support-matrix"></a>Матрица поддержки драйвера Microsoft JDBC Driver for SQL Server
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  В этой статье приведены матрица и политика жизненного цикла поддержки для драйвера Microsoft JDBC Driver for SQL Server.  
  
## <a name="microsoft-jdbc-driver-support-lifecycle-matrix-and-policy"></a>Матрица и политика жизненного цикла поддержки для драйвера Microsoft JDBC  
 Политика жизненного цикла поддержки Майкрософт (MSL) предоставляет понятную и предсказуемую информацию о жизненном цикле поддержки продуктов Майкрософт. Основная фаза поддержки драйверов JDBC версий 3.0, 4.x, 6.x и 7.x длится пять лет с момента выпуска соответствующей версии. Основная фаза поддержки определена на веб-сайте жизненного цикла поддержки Майкрософт.  
  
 Возможность расширенной или настраиваемой поддержки драйвера JDBC не предусмотрена.  
    
 Перечисленные ниже версии драйверов Microsoft JDBC будут поддерживаться до указанной даты окончания поддержки.  
  
|Имя драйвера|Версия пакета драйвера|Применимые JAR(s)|Окончание основной фазы поддержки|
|-|-|-|-|  
|Microsoft JDBC Driver 7.4 для SQL Server|7.4|MSSQL-JDBC-7.4.1. jre12. jar<br> MSSQL-JDBC-7.4.1. jre11. jar<br> MSSQL-JDBC-7.4.1. jre8. jar|2 августа 2024 г.|
|Microsoft JDBC Driver 7.2 для SQL Server|7.2|mssql-jdbc-7.2.2.jre11.jar<br> mssql-jdbc-7.2.2.jre8.jar|16 апреля 2024 г.|
|Драйвер Microsoft JDBC 7.0 для SQL Server|7.0|mssql-jdbc-7.0.0.jre10.jar<br> mssql-jdbc-7.0.0.jre8.jar|31 июля 2023 г.|  
|Драйвер Microsoft JDBC 6.4 для SQL Server|6.4|mssql-jdbc-6.4.0.jre9.jar<br> mssql-jdbc-6.4.0.jre8.jar<br> mssql-jdbc-6.4.0.jre7.jar|27 февраля 2023 г.|    
|Microsoft JDBC Driver 6.2 для SQL Server|6.2|mssql-jdbc-6.2.2.jre8.jar<br> mssql-jdbc-6.2.2.jre7.jar|30 июня 2022 г.|    
|Драйвер Microsoft JDBC Driver 6.0 для SQL Server|6.0|sqljdbc42.jar<br>sqljdbc41.jar|14 июля 2021 г.|    
|Microsoft JDBC Driver 4.2 for SQL Server|4.2|sqljdbc42.jar<br>sqljdbc41.jar|24 августа 2020 г.|  
|Microsoft JDBC Driver 4.1 for SQL Server|4.1|sqljdbc41.jar|12 декабря 2019 г.|  
  
 Следующие драйверы Microsoft JDBC больше не поддерживаются.  
 
|Имя драйвера|Версия пакета драйвера|Окончание основной фазы поддержки|  
|-|-|-|
|Microsoft JDBC Driver 4.0 for SQL Server|4.0|6 марта 2017 г.|  
|Драйвер JDBC 3.0 для Microsoft SQL Server|3.0|23 апреля 2015 г.|  
|Драйвер JDBC 2.0 для Microsoft SQL Server|2.0|31 декабря 2012 г.|  
|Драйвер JDBC 1.2 для Microsoft SQL Server 2005|1.2|25 июня 2011 г.|  
|Драйвер JDBC 1.1 для Microsoft SQL Server 2005|1.1|25 июня 2011 г.|  
|Драйвер JDBC 1.0 для Microsoft SQL Server 2005|1.0|25 июня 2011 г.|  
|Драйвер JDBC для Microsoft SQL Server 2000|2000|9 июля 2010 г.|  
  
## <a name="sql-version-compatibility"></a>Совместимость с версиями SQL  
  
|Версия драйвера|SQL Server 2008|SQL Server 2008 R2|SQL Server 2012|База данных SQL Azure|PDW 2008R2 AU3<sup>4</sup>|SQL Server 2014|SQL Server 2016|SQL Server 2017|SQL Server 2019|  
|-|-|-|-|-|-|-|-|-|-|-|
|7.4|Нет|Нет|Да|Да|Да|Да|Да|Да|Да|
|7.2|Нет|Да|Да|Да|Да|Да|Да|Да|Нет| 
|7.0|Нет|Да|Да|Да|Да|Да|Да|Да|Нет| 
|6.4|Нет|Да|Да|Да|Да|Да|Да|Да|Нет| 
|6.2|Да|Да|Да|Да|Да|Да|Да|Да|Нет|
|6.1|Да|Да|Да|Да|Да|Да|Да|Нет|Нет|
|6.0|Да|Да|Да|Да|Да|Да|Да|Нет|Нет|
|4.2|Да|Да|Да|Да|Да|Да|Да|Нет|Нет|
|4.1|Да|Да|Да|Да|Да|Да|Да|Нет|Нет|
|4.0|Да|Да|Да|Да|Да|Да|Да|Нет|Нет|
|3.0|Да|Да|Да<sup>1</sup>|Да<sup>2</sup>|Нет|Да<sup>5</sup>|Нет|Нет|Нет|
|2.0|Да<sup>3</sup>|Да<sup>3</sup>|Нет|Нет|Нет|Нет|Нет|Нет|Нет|
|1.2|Да<sup>3</sup>|Нет|Нет|Нет|Нет|Нет|Нет|Нет|Нет|
|1.1|Нет|Нет|Нет|Нет|Нет|Нет|Нет|Нет|Нет|  
|1.0|Нет|Нет|Нет|Нет|Нет|Нет|Нет|Нет|Нет|  
|2000|Нет|Нет|Нет|Нет|Нет|Нет|Нет|Нет|Нет|  
  
 <sup>1</sup> Microsoft JDBC Driver для SQL Server версии 3.0 может подключаться к SQL Server 2012 в качестве клиента нижнего уровня.  
  
 <sup>2</sup> В версии 3.0 в форме исправления добавлена поддержка базы данных SQL Azure. Мы рекомендуем пользователям баз данных SQL Azure использовать последнюю версию драйвера.  
  
 <sup>3</sup> Microsoft JDBC Driver для SQL Server версии 2.0 и Microsoft JDBC Driver для SQL Server 2005 версии 1.2 могут подключаться к SQL Server 2008 в качестве клиента нижнего уровня. Когда допускается подключение к клиенту более низкого уровня с последующим преобразованием данных, приложения могут выполнять запросы и выполнять обновления для таких новых типов данных SQL Server 2008: time, date, datetime2, datetimeoffset и FILESTREAM. Дополнительные сведения о том, как использовать эти новые типы данных с помощью драйвера JDBC, см. в статьях  [Working with SQL Server 2008 Date/Time Data Types using v1.2 JDBC driver](https://go.microsoft.com/fwlink/?LinkId=145198) (Использование типов данных Date и Time в SQL Server 2008 с помощью драйвера JDBC 1.2) и  [Working with SQL Server 2008 Filestream using v1.2 JDBC driver](https://go.microsoft.com/fwlink/?LinkId=145199)(Использование типа данных Filestream в SQL Server 2008 с помощью драйвера JDBC). Дополнительные сведения об обратной совместимости новых типов данных см. в статьях  [Использование данных даты и времени](https://go.microsoft.com/fwlink/?LinkId=145211)и  [Поддержка FILESTREAM](https://go.microsoft.com/fwlink/?LinkId=145212) в электронной документации по SQL Server.  
  
 <sup>4</sup> Поддержка подключений между Microsoft JDBC Driver и хранилищем Parallel Data Warehouse была впервые реализована в Microsoft JDBC Driver для SQL Server версии 4.0 и в обновлении 3 для устройства Parallel Data Warehouse в Microsoft SQL Server 2008 R2.  
  
 <sup>5</sup> Microsoft JDBC Driver для SQL Server версии 3.0 может подключаться SQL Server 2014 в качестве клиента нижнего уровня.  
  
## <a name="java-and-jdbc-specification-support"></a>Поддержка спецификаций Java и JDBC  
  
|Версия драйвера JDBC|Версия JRE|Версия API JDBC| 
|-|-|-|  
|7.4|1.8, 11, 12|4.2, 4.3 (частично)|
|7.2|1.8, 11|4.2, 4.3 (частично)|
|7.0|1.8, 10|4.2, 4.3 (частично)|
|6.4|1.7, 1.8, 9|4.1, 4.2, 4.3 (частично)|  
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
 
 