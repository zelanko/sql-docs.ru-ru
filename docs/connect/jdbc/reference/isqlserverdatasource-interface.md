---
title: "Интерфейс ISQLServerDataSource | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba1d3242-19ca-4321-83fe-867a4f69f1d4
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 175e14fbd67d63080a0615d67fd5bf5123612b99
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="isqlserverdatasource-interface"></a>Интерфейс ISQLServerDataSource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Фабрика для создания соединений с источником данных, представленным данным объектом. Этот интерфейс добавлен в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] версии 3.0 драйвера JDBC.  
  
 **Пакет:** com.microsoft.sqlserver.jdbc  
  
 **Расширяет:** java.sql.CommonDataSource  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public interface ISQLServerDataSource  
```  
  
## <a name="remarks"></a>Замечания  
 Этот интерфейс реализуется [класса SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).  
  
 Этот интерфейс предоставляет следующие [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-определенных методов:  
  
|Метод|Дополнительные сведения см. в разделе|  
|------------|-------------------------------|  
|public String getApplicationName()|[getApplicationName](../../../connect/jdbc/reference/getapplicationname-method-sqlserverdatasource.md)|  
|public String getDatabaseName()|[getDatabaseName](../../../connect/jdbc/reference/getdatabasename-method-sqlserverdatasource.md)|  
|public String getDescription()|[getDescription](../../../connect/jdbc/reference/getdescription-method-sqlserverdatasource.md)|  
|public boolean getEncrypt()|[getEncrypt](../../../connect/jdbc/reference/getencrypt-method-sqlserverdatasource.md)|  
|public String getFailoverPartner()|[getFailoverPartner](../../../connect/jdbc/reference/getfailoverpartner-method-sqlserverdatasource.md)|  
|public String getHostNameInCertificate()|[getHostNameInCertificate](../../../connect/jdbc/reference/gethostnameincertificate-method-sqlserverdatasource.md)|  
|public String getInstanceName()|[getInstanceName](../../../connect/jdbc/reference/getinstancename-method-sqlserverdatasource.md)|  
|public boolean getLastUpdateCount()|[getLastUpdateCount](../../../connect/jdbc/reference/getlastupdatecount-method-sqlserverdatasource.md)|  
|public int getLockTimeout()|[getLockTimeout](../../../connect/jdbc/reference/getlocktimeout-method-sqlserverdatasource.md)|  
|public boolean getMultiSubnetFailover()|[getMultiSubnetFailover](../../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md)|  
|public int getPacketSize()|[getPacketSize](../../../connect/jdbc/reference/getpacketsize-method-sqlserverdatasource.md)|  
|public int getPortNumber()|[getPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md)|  
|public String getResponseBuffering()|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverdatasource.md)|  
|public String getSelectMethod()|[метод getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md)|  
|public boolean getSendStringParametersAsUnicode()|[getSendStringParametersAsUnicode](../../../connect/jdbc/reference/getsendstringparametersasunicode-method-sqlserverdatasource.md)|  
|public boolean getSendTimeAsDatetime()|[getSendTimeAsDatetime](../../../connect/jdbc/reference/getsendtimeasdatetime-method-sqlserverdatasource.md)|  
|public String getServerName()|[getServerName](../../../connect/jdbc/reference/getservername-method-sqlserverdatasource.md)|  
|public boolean getTrustServerCertificate()|[getTrustServerCertificate](../../../connect/jdbc/reference/gettrustservercertificate-method-sqlserverdatasource.md)|  
|public String getTrustStore()|[getTrustStore](../../../connect/jdbc/reference/gettruststore-method-sqlserverdatasource.md)|  
|public String getURL()|[getURL](../../../connect/jdbc/reference/geturl-method-sqlserverdatasource.md)|  
|public String getUser()|[getUser](../../../connect/jdbc/reference/getuser-method-sqlserverdatasource.md)|  
|public String getWorkstationID()|[getWorkstationID](../../../connect/jdbc/reference/getworkstationid-method-sqlserverdatasource.md)|  
|public boolean getXopenStates()|[getXopenStates](../../../connect/jdbc/reference/getxopenstates-method-sqlserverdatasource.md)|  
|public void setApplicationName(String)|[setApplicationName](../../../connect/jdbc/reference/setapplicationname-method-sqlserverdatasource.md)|  
|public void setAuthenticationSceme(String)|[setAuthenticationSceme](../../../connect/jdbc/reference/setauthenticationscheme-sqlserverdatasource.md)|  
|public void setDatabaseName(String)|[setDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md)|  
|public void setDescription(String)|[Описание](../../../connect/jdbc/reference/setdescription-method-sqlserverdatasource.md)|  
|public void setEncrypt(boolean)|[setEncrypt](../../../connect/jdbc/reference/setencrypt-method-sqlserverdatasource.md)|  
|public void setFailoverPartner(String)|[setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md)|  
|public void setHostNameInCertificate(String)|[setHostNameInCertificate](../../../connect/jdbc/reference/sethostnameincertificate-method-sqlserverdatasource.md)|  
|public void setInstanceName(String)|[setInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md)|  
|public void setIntegratedSecurity(boolean)|[setIntegratedSecurity](../../../connect/jdbc/reference/setintegratedsecurity-method-sqlserverdatasource.md)|  
|public void setLastUpdateCount(boolean)|[setLastUpdateCount](../../../connect/jdbc/reference/setlastupdatecount-method-sqlserverdatasource.md)|  
|public void setLockTimeout(int)|[setLockTimeout](../../../connect/jdbc/reference/setlocktimeout-method-sqlserverdatasource.md)|  
|public void setMultiSubnetFailover(boolean multiSubnetFailover)|[setMultiSubnetFailover](../../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md)|  
|public void setPacketSize(int)|[setPacketSize](../../../connect/jdbc/reference/setpacketsize-method-sqlserverdatasource.md)|  
|public void setPassword(String)|[Задание пароля](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md)|  
|public void setPortNumber(int)|[setPortNumber](../../../connect/jdbc/reference/setportnumber-method-sqlserverdatasource.md)|  
|public void setResponseBuffering(String)|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverdatasource.md)|  
|public void setSelectMethod(String)|[setSelectMethod](../../../connect/jdbc/reference/setselectmethod-method-sqlserverdatasource.md)|  
|public void setSendStringParametersAsUnicode(boolean)|[setSendStringParametersAsUnicode](../../../connect/jdbc/reference/setsendstringparametersasunicode-method-sqlserverdatasource.md)|  
|public void setSendTimeAsDatetime(boolean)|[setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md)|  
|public void setServerName(String)|[setServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md)|  
|public void setTrustServerCertificate(boolean)|[setTrustServerCertificate](../../../connect/jdbc/reference/settrustservercertificate-method-sqlserverdatasource.md)|  
|public void setTrustStore(String)|[setTrustStore](../../../connect/jdbc/reference/settruststore-method-sqlserverdatasource.md)|  
|public void setTrustStorePassword(String)|[setTrustStorePassword](../../../connect/jdbc/reference/settruststorepassword-method-sqlserverdatasource.md)|  
|public void setURL(String url)|[setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md)|  
|public void setUser(String)|[Инструкция setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md)|  
|public void setWorkstationID(String)|[setWorkstationID](../../../connect/jdbc/reference/setworkstationid-method-sqlserverdatasource.md)|  
|public void setXopenStates(boolean)|[setXopenStates](../../../connect/jdbc/reference/setxopenstates-method-sqlserverdatasource.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API для драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  

