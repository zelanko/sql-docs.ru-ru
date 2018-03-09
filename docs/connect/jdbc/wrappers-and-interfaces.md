---
title: "Оболочки и интерфейсы | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27fc9b72-9f21-4728-abcb-5c015f28a6ab
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6b0dc608dc62db0f8f06092843c0c2a0e7b747ca
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="wrappers-and-interfaces"></a>Оболочки и интерфейсы
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Поддерживает интерфейсы, позволяющие создавать классы-посредники и оболочки, позволяющие доступа к расширениям API-интерфейса JDBC, характерные для [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] через прокси-интерфейса.  
  
## <a name="wrappers"></a>Оболочки  
 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Поддерживает интерфейс java.sql.Wrapper. Этот интерфейс обеспечивает механизм для расширения доступа к API-интерфейса JDBC, характерные для [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] через прокси-интерфейса.  
  
 Интерфейс java.sql.Wrapper определяет два метода: **isWrapperFor** и **unwrap**. **IsWrapperFor** метод проверяет, реализует ли указанный объект ввода данный интерфейс. **Unwrap** метод возвращает объект, реализующий этот интерфейс, чтобы разрешить доступ к [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] определенных методов.  
  
 **isWrapperFor** и **unwrap** методы предоставляются следующим образом:  
  
-   [Метод isWrapperFor &#40; SQLServerCallableStatement &#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlservercallablestatement.md)  
  
-   [Извлечение из оболочки метод &#40; SQLServerCallableStatement &#41;](../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md)  
  
-   [Метод isWrapperFor &#40; SQLServerConnectionPoolDataSource &#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverconnectionpooldatasource.md)  
  
-   [Извлечение из оболочки метод &#40; SQLServerConnectionPoolDataSource &#41;](../../connect/jdbc/reference/unwrap-method-sqlserverconnectionpooldatasource.md)  
  
-   [Метод isWrapperFor &#40; SQLServerDataSource &#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverdatasource.md)  
  
-   [Извлечение из оболочки метод &#40; SQLServerDataSource &#41;](../../connect/jdbc/reference/unwrap-method-sqlserverdatasource.md)  
  
-   [Метод isWrapperFor &#40; SQLServerPreparedStatement &#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverpreparedstatement.md)  
  
-   [Извлечение из оболочки метод &#40; SQLServerPreparedStatement &#41;](../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md)  
  
-   [Метод isWrapperFor &#40; SQLServerStatement &#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md)  
  
-   [Извлечение из оболочки метод &#40; SQLServerStatement &#41;](../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md)  
  
-   [Метод isWrapperFor &#40; SQLServerXADataSource &#41;](../../connect/jdbc/reference/iswrapperfor-method-sqlserverxadatasource.md)  
  
-   [Извлечение из оболочки метод &#40; SQLServerXADataSource &#41;](../../connect/jdbc/reference/unwrap-method-sqlserverxadatasource.md)  
  
## <a name="interfaces"></a>Интерфейсы  
 Начиная с версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] версии 3.0 драйвера JDBC, доступны интерфейсы для сервера приложений для доступа к методу, определяемому драйвером из связанного класса. Сервер приложений может поместить класс в оболочку, создав класс-посредник, обеспечивающий [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]-определенных функциональных возможностей интерфейса. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Поддерживает интерфейсы, имеющие [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] методы и константы, сервер приложений может создать прокси-класса.  
  
 Интерфейсы являются производными от стандартных Java-интерфейсов, можно использовать тот же объект после оболочки для доступа к функции драйвера или универсальный интерфейс [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] функциональные возможности.  
  
 Добавлены следующие интерфейсы:  
  
-   [ISQLServerCallableStatement](../../connect/jdbc/reference/isqlservercallablestatement-interface.md)  
  
-   [ISQLServerConnection](../../connect/jdbc/reference/isqlserverconnection-interface.md)  
  
-   [ISQLServerDataSource](../../connect/jdbc/reference/isqlserverdatasource-interface.md)  
  
-   [ISQLServerPreparedStatement](../../connect/jdbc/reference/isqlserverpreparedstatement-interface.md)  
  
-   [ISQLServerResultSet](../../connect/jdbc/reference/isqlserverresultset-interface.md)  
  
-   [ISQLServerStatement](../../connect/jdbc/reference/isqlserverstatement-interface.md)  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Description  
 В этом примере показано, как получить доступ к [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]-определенной функции из объекта источника данных. Этот класс источник данных может быть были в оболочку сервером приложений. Для доступа к функции драйвера JDBC или константа, можно снять оболочку с datasource для интерфейса ISQLServerDataSource и использовать функции, объявленные в этом интерфейсе.  
  
### <a name="code"></a>код  
  
```  
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
  
## <a name="see-also"></a>См. также:  
 [Основные сведения о типах данных драйвера JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
