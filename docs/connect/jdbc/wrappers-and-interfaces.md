---
description: Оболочки и интерфейсы
title: Программы-оболочки и интерфейсы | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 27fc9b72-9f21-4728-abcb-5c015f28a6ab
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 504527843063bb3d5e3fd4a8c284dfc5e8e25b12
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450056"
---
# <a name="wrappers-and-interfaces"></a>Оболочки и интерфейсы

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] поддерживает интерфейсы, позволяющие создавать классы-посредники и оболочки для доступа к расширениям API JDBC, определяемым драйвером [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], через интерфейс-посредник.

## <a name="wrappers"></a>Оболочки

Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] поддерживает интерфейс java.sql.Wrapper. Этот интерфейс обеспечивает механизм доступа к расширениям API JDBC, определяемым драйвером [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], через интерфейс-посредник.

Интерфейс Java. SQL. оберток определяет два метода: **isWrapperFor** и **Unwrap**. Метод **isWrapperFor** проверяет, реализует ли указанный объект ввода данный интерфейс. Метод **unwrap** возвращает объект, в котором реализован указанный интерфейс, для обеспечения доступа к методам, определяемым драйвером [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].

Методы **isWrapperFor** и **unwrap** предоставляются следующим образом:

- [Метод isWrapperFor &#40;SQLServerCallableStatement&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlservercallablestatement.md)

- [Метод unwrap (SQLServerCallableStatement)](../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md)

- [Метод isWrapperFor &#40;SQLServerConnectionPoolDataSource&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverconnectionpooldatasource.md)

- [Метод unwrap (SQLServerConnectionPoolDataSource)](../../connect/jdbc/reference/unwrap-method-sqlserverconnectionpooldatasource.md)

- [Метод isWrapperFor (SQLServerDataSource)](../../connect/jdbc/reference/iswrapperfor-method-sqlserverdatasource.md)

- [Метод unwrap (SQLServerDataSource)](../../connect/jdbc/reference/unwrap-method-sqlserverdatasource.md)

- [Метод isWrapperFor (SQLServerPreparedStatement)](../../connect/jdbc/reference/iswrapperfor-method-sqlserverpreparedstatement.md)

- [Метод unwrap &#40;SQLServerPreparedStatement&#41;](../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md)

- [Метод isWrapperFor &#40;SQLServerStatement&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md)

- [Метод unwrap (SQLServerStatement)](../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md)

- [Метод isWrapperFor &#40;SQLServerXADataSource&#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverxadatasource.md)

- [Метод unwrap (SQLServerXADataSource)](../../connect/jdbc/reference/unwrap-method-sqlserverxadatasource.md)

## <a name="interfaces"></a>интерфейсов,

Начиная с версии 3.0 драйвера JDBC для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] доступны интерфейсы для сервера приложений, позволяющие осуществлять доступ к методу, определяемому драйвером, из связанного класса. Сервер приложений может поместить класс в оболочку, создав класс-посредник, обеспечивающий определяемые драйвером [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] функции через интерфейс. Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] поддерживает интерфейсы, имеющие методы и константы, определяемые драйвером [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], что позволяет серверу приложений создать для класса класс-посредник.

Эти интерфейсы являются производными от стандартных интерфейсов Java, поэтому тот же объект может быть использован и после получения из оболочки для доступа к функциям, определяемым драйвером, либо к стандартным функциям драйвера [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].

Добавлены следующие интерфейсы:

- [ISQLServerCallableStatement](../../connect/jdbc/reference/isqlservercallablestatement-interface.md)

- [ISQLServerConnection](../../connect/jdbc/reference/isqlserverconnection-interface.md)

- [ISQLServerDataSource](../../connect/jdbc/reference/isqlserverdatasource-interface.md)

- [ISQLServerPreparedStatement](../../connect/jdbc/reference/isqlserverpreparedstatement-interface.md)

- [ISQLServerResultSet](../../connect/jdbc/reference/isqlserverresultset-interface.md)

- [ISQLServerStatement](../../connect/jdbc/reference/isqlserverstatement-interface.md)

## <a name="example"></a>Пример

### <a name="description"></a>Описание

В образце показано, как получить доступ к функции, определяемой драйвером [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], через объект DataSource. Класс DataSource может быть помещен в оболочку сервером приложений. Для доступа к функции или константе, определяемой драйвером JDBC, можно снять оболочку с datasource для интерфейса ISQLServerDataSource и использовать функции, объявленные в данном интерфейсе.

### <a name="code"></a>Код

```java
import javax.sql.*;  
import java.sql.*;  
import com.microsoft.sqlserver.jdbc.*;  

public class UnWrapTest {  
   public static void main(String[] args) {  
      // This is a test.  This DataSource object could be something from an appserver
      // which has wrapped the real SQLServerDataSource with its own wrapper  
      SQLServerDataSource ds = new SQLServerDataSource();  
      checkSendStringParametersAsUnicode(ds);  
   }  

   // Unwrap to the ISQLServerDataSource interface to access the getSendStringParametersAsUnicode function  
   static void checkSendStringParametersAsUnicode(DataSource ds) {  
      try {  
         final ISQLServerDataSource sqlServerDataSource = ds.unwrap(ISQLServerDataSource.class);  
         boolean sendStringParametersAsUnicode = sqlServerDataSource.getSendStringParametersAsUnicode();  

         System.out.println("Send string as parameter value is:-" + sendStringParametersAsUnicode);  

      } catch (SQLException sqlE) {  
         System.out.println("Exception:-" + sqlE);  
      }  
   }  
}  
```

## <a name="see-also"></a>См. также раздел

[Основные сведения о типах данных JDBC Driver](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)
