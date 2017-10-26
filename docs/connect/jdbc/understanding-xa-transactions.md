---
title: "Основные сведения о транзакциях XA | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 574e326f-0520-4003-bdf1-62d92c3db457
caps.latest.revision: 80
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b1ceff7c271688fcabf3206c4ba1fe0147e2afe4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="understanding-xa-transactions"></a>Основные сведения о транзакциях XA
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Обеспечивает поддержку Java Platform, Enterprise Edition/JDBC 2.0 дополнительных распределенных транзакций. Соединения JDBC, получаемые из [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md) класса могут участвовать в стандартных средах, например, Enterprise Edition (Java EE) серверах приложений платформы Java обработки распределенных транзакций.  
  
> [!WARNING]  
>  Драйвер Microsoft JDBC Driver 4.2 (и более поздние версии) для SQL включает новые параметры времени ожидания для существующей функции для автоматического отката неподготовленных транзакций. В разделе [Настройка параметров времени ожидания сервера для автоматического отката неподготовленных транзакций](../../connect/jdbc/understanding-xa-transactions.md#BKMK_ServerSide) далее в этом разделе для получения дополнительных сведений.  
  
## <a name="remarks"></a>Замечания  
 Далее представлены классы для реализации распределенных транзакций.  
  
|Class|Реализации|Description|  
|-----------|----------------|-----------------|  
|com.microsoft.sqlserver.jdbc.SQLServerXADataSource|javax.sql.XADataSource|Фабрика класса для распределенных соединений.|  
|com.microsoft.sqlserver.jdbc.SQLServerXAResource|javax.transaction.xa.XAResource|Адаптер ресурсов для диспетчера транзакций.|  
  
> [!NOTE]  
>  Для соединений распределенных транзакций XA по умолчанию устанавливается уровень изоляции Read Committed.  
  
## <a name="guidelines-and-limitations-when-using-xa-transactions"></a>Правила и ограничения на использование транзакций XA  
 К сильно связанным транзакциям относятся следующие дополнительные рекомендации.  
  
-   Если транзакции XA используются вместе с координатором распределенных транзакций (Майкрософт) (MS DTC), то текущая версия MS DTC может не поддерживать сильно связанные ветви XA. Например, в MS DTC действует взаимно однозначное сопоставление между идентификатором ветви транзакции XA (XID) и идентификатором транзакции MS DTC, и работа, выполняемая слабосвязанными ветвями XA, изолируется.  
  
     Исправление, предоставляемое в [MSDTC and Tightly Coupled Transactions](http://support.microsoft.com/kb/938653) обеспечивает поддержку сильно связанных ветвей XA, когда несколько ветвей XA с одинаковые глобальные Идентификаторы транзакции (GTRID) сопоставляются с одним идентификатором транзакции MS DTC. Эта поддержка позволяет нескольких сильно связанных ветвей XA для просмотра изменений друг друга в диспетчере ресурсов, таких как [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   Объект [SSTRANSTIGHTLYCPLD](../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md) флаг позволяет приложениям использовать тесно связанные транзакции XA, имеющие разные XA идентификаторы ветвей транзакции (BQUAL), но одинаковые глобальные Идентификаторы транзакции (GTRID) и идентификатор формата (FormatID). Для использования этой функции необходимо задать [SSTRANSTIGHTLYCPLD](../../connect/jdbc/reference/sstranstightlycpld-field-sqlserverxaresource.md) в параметре флаги XAResource.start метода:  
  
    ```  
    xaRes.start(xid, SQLServerXAResource.SSTRANSTIGHTLYCPLD);  
    ```  
  
## <a name="configuration-instructions"></a>Инструкции по настройке  
 Если источники данных XA нужно использовать вместе с координатором распределенных транзакций (Майкрософт) (MS DTC) для обработки распределенных транзакций, необходимо выполнить следующие действия.  
  
> [!NOTE]  
>  Компоненты распределенных транзакций JDBC находятся в каталоге XA в каталоге установки драйвера JDBC. К этим компонентам относятся файлы xa_install.sql и sqljdbc_xa.dll.  
  
### <a name="running-the-ms-dtc-service"></a>Запуск службы MS DTC  
 Службы MS DTC должен быть помечен как **автоматического** в Service Manager, чтобы убедиться, что он работает, когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] запуска службы. Чтобы включить MS DTC для транзакций XA, необходимо выполнить следующие действия.  
  
 В Windows Vista и более поздних версиях:  
  
1.  Нажмите кнопку **запустить** кнопку, введите **dcomcnfg** в начале **поиска** и нажмите клавишу ВВОД, чтобы открыть **служб компонентов**. Также можно ввести %windir%\system32\comexp.msc в **начатьпоиск** поле, чтобы открыть **служб компонентов**.  
  
2.  Разверните узлы "Службы компонентов", "Компьютеры", "Мой компьютер" и "Координатор распределенных транзакций".  
  
3.  Щелкните правой кнопкой мыши **Локальная DTC** , а затем выберите **свойства**.  
  
4.  Нажмите кнопку **безопасности** на вкладке **свойства: Локальная DTC** диалоговое окно.  
  
5.  Выберите **включить транзакции XA** флажок и нажмите кнопку **ОК**. Это приведет к перезапуску службы MS DTC.  
  
6.  Нажмите кнопку **ОК** , чтобы закрыть **свойства** диалоговое окно, а затем закройте **служб компонентов**.  
  
7.  Остановите и перезапустите [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] чтобы убедиться в том, что синхронизацию с изменениями MS DTC.  
  
### <a name="configuring-the-jdbc-distributed-transaction-components"></a>Настройка компонентов распределенных транзакций JDBC  
 Чтобы настроить компоненты распределенных транзакций драйвера JDBC, можно выполнить следующие действия  
  
1.  Скопируйте новый файл sqljdbc_xa.dll из каталога установки драйвера JDBC в каталог Binn на каждом [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] компьютера, который будет участвовать в распределенных транзакциях.  
  
    > [!NOTE]  
    >  Если транзакции XA используются с 32-разрядной версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], используйте файл sqljdbc_xa.dll из x86 папки, даже если [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] устанавливается на x64 процессора. Если транзакции XA используются с 64-разрядной версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] на x64 процессор, используйте файл sqljdbc_xa.dll из x64 папки.  
  
2.  Выполните скрипт базы данных xa_install.sql в каждом [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] экземпляр, который будет участвовать в распределенных транзакциях. Этот скрипт устанавливает расширенные хранимые процедуры, которые вызываются из sqljdbc_xa.dll. Эти расширенные хранимые процедуры реализуют распределенной транзакции и поддержку XA [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]. Необходимо выполнять от имени администратора [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] экземпляра.  
  
3.  Чтобы предоставить определенному пользователю разрешения для участия в распределенных транзакциях через драйвер JDBC, его необходимо включить в роль SqlJDBCXAUser.  
  
 Можно настроить только одну версию сборки sqljdbc_xa.dll на каждом [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] экземпляра за раз. Приложения нужно использовать различные версии драйвера JDBC для подключения к тому же [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] экземпляра с помощью соединения XA. В этом случае файл sqljdbc_xa.dll, который содержит самую новую версию драйвера JDBC, должны устанавливаться на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] экземпляра.  
  
 Существует три способа, чтобы проверить версию файла sqljdbc_xa.dll на установлена [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] экземпляр:  
  
1.  Откройте каталог LOG [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] компьютера, который будет участвовать в распределенных транзакциях. Выберите и откройте [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] файл «ERRORLOG». Найдите в файле ERRORLOG фразу "Используется SQLJDBC_XA.dll версии...".  
  
2.  Откройте каталог Binn [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] компьютера, который будет участвовать в распределенных транзакциях. Выберите сборку sqljdbc_xa.dll.  
  
    -   В Windows Vista и более поздних версиях: щелкните правой кнопкой мыши файл sqljdbc_xa.dll и выберите пункт меню «Свойства». Нажмите кнопку **сведения** вкладки. **Версия файла** поле показана версия файла sqljdbc_xa.dll, которая установлена на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] экземпляра.  
  
3.  Настройте ведение журнала, как показано в примере кода в следующем разделе. Найдите в выходном файле журнала фразу «Версия XA DLL на сервере:...».  
  
###  <a name="BKMK_ServerSide"></a>Настройка параметров времени ожидания сервера для автоматического отката неподготовленных транзакций  
  
> [!WARNING]  
>  Этот серверный параметр обновился с Microsoft JDBC Driver 4.2 (и более поздней версии) для SQL Server. Чтобы это обновленное поведение работало, убедитесь, что файл sqljdbc_xa.dll на сервере обновлен. Дополнительные сведения о настройке времени ожидания на стороне клиента см. в разделе [XAResource.setTransactionTimeout()](http://docs.oracle.com/javase/8/docs/api/javax/transaction/xa/XAResource.html).  
  
 Существует два параметра реестра (типа DWORD) для управления временем ожидания распределенных транзакций.  
  
-   **XADefaultTimeout** (в секундах): значение времени ожидания по умолчанию для использования, когда пользователь не указывает время ожидания. Значение по умолчанию равно 0.  
  
-   **XAMaxTimeout** (в секундах): максимальное значение времени ожидания, которое может задать пользователь. Значение по умолчанию равно 0.  
  
 Эти параметры относятся к экземпляру SQL Server и должны быть созданы в следующем разделе реестра:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL\<**версии**>.\< *имя_экземпляра*> \XATimeout  
  
> [!NOTE]  
>  Параметры реестра для 32-разрядных SQL Server на 64-разрядных компьютерах, необходимо создать в следующем разделе: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Microsoft SQL Server\MSSQL\<версии >. < имя_экземпляра > \ XATimeout  
  
 Время ожидания задается для каждой транзакции, когда она запускается; по истечении времени ожидания выполняется откат транзакции в SQL Server. Время ожидания зависит от параметров реестра и указанных пользователем параметров в XAResource.setTransactionTimeout(). Вот несколько примеров интерпретации таких значений времени ожидания.  
  
-   XADefaultTimeout = 0, XAMaxTimeout = 0  
  
     Время ожидания по умолчанию не будет использоваться, максимальное время ожидания не будет применяться к клиентам. В этом случае у транзакций будет время ожидания, только если клиент устанавливает время ожидания с помощью XAResource.setTransactionTimeout.  
  
-   XADefaultTimeout = 60, XAMaxTimeout = 0  
  
     Время ожидания всех транзакций будет равно 60 секундам, если клиент не указывает время ожидания. Если клиент указывает время ожидания, будет использоваться это значение времени ожидания. Максимальное значение времени ожидания не применяется.  
  
-   XADefaultTimeout = 30, XAMaxTimeout = 60  
  
     Время ожидания всех транзакций будет равно 30 секундам, если клиент не указывает время ожидания. Если клиент указывает время ожидания, будет использоваться время ожидания клиента, если оно менее 60 секунд (максимальное значение).  
  
-   XADefaultTimeout = 0, XAMaxTimeout = 30  
  
     Время ожидания всех транзакций будет равно 30 секундам (максимальное значение), если клиент не указывает время ожидания. Если клиент указывает время ожидания, будет использоваться время ожидания клиента, если оно менее 30 секунд (максимальное значение).  
  
### <a name="upgrading-sqljdbcxadll"></a>Обновление файла sqljdbc_xa.dll  
 При установке новой версии драйвера JDBC также следует обновить файл sqljdbc_xa.dll, расположенный на сервере, с помощью файла sqljdbc_xa.dll из этой новой версии.  
  
> [!IMPORTANT]  
>  Файл sqljdbc_xa.dll следует обновлять во время планового обслуживания либо в случае, если не выполняется ни одной транзакции MS DTC.  
  
1.  Выгрузить файл sqljdbc_xa.dll с помощью [!INCLUDE[tsql](../../includes/tsql_md.md)] команда **sqljdbc_xa DBCC (FREE)**.  
  
2.  Скопируйте новый файл sqljdbc_xa.dll из каталога установки драйвера JDBC в каталог Binn на каждом [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] компьютера, который будет участвовать в распределенных транзакциях.  
  
     Новый файл DLL будет загружаться при вызове расширенной процедуры в sqljdbc_xa.dll. Необходимо перезапустить [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] для загрузки новых определений.  
  
### <a name="configuring-the-user-defined-roles"></a>Настройка определяемых пользователем ролей  
 Чтобы предоставить определенному пользователю разрешения для участия в распределенных транзакциях через драйвер JDBC, его необходимо включить в роль SqlJDBCXAUser. Например, используйте следующую [!INCLUDE[tsql](../../includes/tsql_md.md)] код, чтобы добавить пользователя с именем «shelby» (стандартное имя входа пользователя SQL «shelby») в роль SqlJDBCXAUser:  
  
```  
USE master  
GO  
EXEC sp_grantdbaccess 'shelby', 'shelby'  
GO  
EXEC sp_addrolemember [SqlJDBCXAUser], 'shelby'  
```  
  
 Определяемые пользователем роли SQL определяются в рамках базы данных. Чтобы создать собственную роль в целях безопасности, необходимо определить роль в каждой базе данных и добавлять пользователей отдельно для каждой базы данных. Роль SqlJDBCXAUser строго определена в базе данных master, поскольку она используется для предоставления доступа к расширенным хранимым процедурам SQL JDBC, располагающимся в базе данных master. Сначала необходимо предоставить отдельным пользователям доступ к базе данных master, а затем выполнить вход в базу данных master и предоставить этим пользователям доступ к роли SqlJDBCXAUser.  
  
## <a name="example"></a>Пример  
  
```  
import java.net.Inet4Address;  
import java.sql.*;  
import java.util.Random;  
import javax.transaction.xa.*;  
import javax.sql.*;  
import com.microsoft.sqlserver.jdbc.*;  
  
public class testXA {  
  
   public static void main(String[] args) throws Exception {  
  
      // Create variables for the connection string.  
      String prefix = "jdbc:sqlserver://";  
      String serverName = "localhost";  
      int portNumber = 1433;  
      String databaseName = "AdventureWorks";   
      String user = "UserName";   
      String password = "*****";  
      String connectionUrl = prefix + serverName + ":" + portNumber  
         + ";databaseName=" + databaseName + ";user=" + user + ";password=" + password;  
  
      try {  
         // Establish the connection.  
         Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
         Connection con = DriverManager.getConnection(connectionUrl);  
  
         // Create a test table.  
         Statement stmt = con.createStatement();  
         try {  
            stmt.executeUpdate("DROP TABLE XAMin");   
         }  
         catch (Exception e) {  
         }  
         stmt.executeUpdate("CREATE TABLE XAMin (f1 int, f2 varchar(max))");  
         stmt.close();  
         con.close();  
  
         // Create the XA data source and XA ready connection.  
         SQLServerXADataSource ds = new SQLServerXADataSource();  
         ds.setUser(user);  
         ds.setPassword(password);  
         ds.setServerName(serverName);  
         ds.setPortNumber(portNumber);  
         ds.setDatabaseName(databaseName);  
         XAConnection xaCon = ds.getXAConnection();  
         con = xaCon.getConnection();  
  
         // Get a unique Xid object for testing.  
         XAResource xaRes = null;  
         Xid xid = null;  
         xid = XidImpl.getUniqueXid(1);  
  
         // Get the XAResource object and set the timeout value.  
         xaRes = xaCon.getXAResource();  
         xaRes.setTransactionTimeout(0);  
  
         // Perform the XA transaction.  
         System.out.println("Write -> xid = " + xid.toString());  
         xaRes.start(xid,XAResource.TMNOFLAGS);  
         PreparedStatement pstmt =   
         con.prepareStatement("INSERT INTO XAMin (f1,f2) VALUES (?, ?)");  
         pstmt.setInt(1,1);  
         pstmt.setString(2,xid.toString());  
         pstmt.executeUpdate();  
  
         // Commit the transaction.  
         xaRes.end(xid,XAResource.TMSUCCESS);  
         xaRes.commit(xid,true);  
  
         // Cleanup.  
         con.close();  
         xaCon.close();  
  
         // Open a new connection and read back the record to verify that it worked.  
         con = DriverManager.getConnection(connectionUrl);  
         ResultSet rs = con.createStatement().executeQuery("SELECT * FROM XAMin");  
         rs.next();  
         System.out.println("Read -> xid = " + rs.getString(2));  
         rs.close();  
         con.close();  
      }   
  
      // Handle any errors that may have occurred.  
      catch (Exception e) {  
         e.printStackTrace();  
      }  
   }  
}  
  
class XidImpl implements Xid {  
  
   public int formatId;  
   public byte[] gtrid;  
   public byte[] bqual;  
   public byte[] getGlobalTransactionId() {return gtrid;}  
   public byte[] getBranchQualifier() {return bqual;}  
   public int getFormatId() {return formatId;}  
  
   XidImpl(int formatId, byte[] gtrid, byte[] bqual) {  
      this.formatId = formatId;  
      this.gtrid = gtrid;  
      this.bqual = bqual;  
   }  
  
   public String toString() {  
      int hexVal;  
      StringBuffer sb = new StringBuffer(512);  
      sb.append("formatId=" + formatId);  
      sb.append(" gtrid(" + gtrid.length + ")={0x");  
      for (int i=0; i<gtrid.length; i++) {  
         hexVal = gtrid[i]&0xFF;  
         if ( hexVal < 0x10 )  
            sb.append("0" + Integer.toHexString(gtrid[i]&0xFF));  
         else  
            sb.append(Integer.toHexString(gtrid[i]&0xFF));  
         }  
         sb.append("} bqual(" + bqual.length + ")={0x");  
         for (int i=0; i<bqual.length; i++) {  
            hexVal = bqual[i]&0xFF;  
            if ( hexVal < 0x10 )  
               sb.append("0" + Integer.toHexString(bqual[i]&0xFF));  
            else  
               sb.append(Integer.toHexString(bqual[i]&0xFF));  
         }  
         sb.append("}");  
         return sb.toString();  
      }  
  
      // Returns a globally unique transaction id.  
      static byte [] localIP = null;  
      static int txnUniqueID = 0;  
      static Xid getUniqueXid(int tid) {  
  
      Random rnd = new Random(System.currentTimeMillis());  
      txnUniqueID++;  
      int txnUID = txnUniqueID;  
      int tidID = tid;  
      int randID = rnd.nextInt();  
      byte[] gtrid = new byte[64];  
      byte[] bqual = new byte[64];  
      if ( null == localIP) {  
         try {  
            localIP = Inet4Address.getLocalHost().getAddress();  
         }  
         catch ( Exception ex ) {  
            localIP =  new byte[] { 0x01,0x02,0x03,0x04 };  
         }  
      }  
      System.arraycopy(localIP,0,gtrid,0,4);  
      System.arraycopy(localIP,0,bqual,0,4);  
  
      // Bytes 4 -> 7 - unique transaction id.  
      // Bytes 8 ->11 - thread id.  
      // Bytes 12->15 - random number generated by using seed from current time in milliseconds.  
      for (int i=0; i<=3; i++) {  
         gtrid[i+4] = (byte)(txnUID%0x100);  
         bqual[i+4] = (byte)(txnUID%0x100);  
         txnUID >>= 8;  
         gtrid[i+8] = (byte)(tidID%0x100);  
         bqual[i+8] = (byte)(tidID%0x100);  
         tidID >>= 8;  
         gtrid[i+12] = (byte)(randID%0x100);  
         bqual[i+12] = (byte)(randID%0x100);  
         randID >>= 8;  
      }  
      return new XidImpl(0x1234, gtrid, bqual);  
   }  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Выполнение транзакций с драйвером JDBC](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)  
  
  

