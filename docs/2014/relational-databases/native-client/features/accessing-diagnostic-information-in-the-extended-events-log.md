---
title: Доступ к диагностическим сведениям в журнале расширенных событий | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: aaa180c2-5e1a-4534-a125-507c647186ab
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ddb50c8993de72230e97cdde729416258272bb1e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63046383"
---
# <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>Доступ к диагностическим сведениям в журнале расширенных событий
  Начиная с версии [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], Native Client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и отслеживание доступа к данным ([Трассировка доступа к данным](https://go.microsoft.com/fwlink/?LinkId=125805)) обновлены. Упрощено получение диагностических сведений об ошибках подключения из кольцевого буфера соединений и сведений о производительности приложений из журнала расширенных событий.  
  
 Дополнительные сведения о чтении журнала расширенных событий см. в разделе [View Event Session Data](../../../database-engine/view-event-session-data.md).  
  
> [!NOTE]  
>  Эта функция предназначена только для диагностики и устранения неполадок; она может оказаться неприменимой для целей аудита или обеспечения безопасности.  
  
## <a name="remarks"></a>Remarks  
 Для операций подключения собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] будет отправлять идентификатор подключения клиента. В случае сбоя подключения можно получить доступ к кольцевому буферу подключения ([Устранение неполадок подключения в SQL Server 2008 с помощью кольцевого буфера подключения](https://go.microsoft.com/fwlink/?LinkId=207752)), найти `ClientConnectionID` поле и получить диагностические сведения об ошибке подключения. Идентификаторы подключений клиентов регистрируются в кольцевом буфере только при возникновении ошибки. (Если соединение не будет отправлено до отправки пакета с предварительным именем, идентификатор подключения клиента не создается.) Идентификатор подключения клиента — это 16-байтовый идентификатор GUID. Идентификатор подключения клиента также можно найти в расположении вывода расширенных событий, если действие `client_connection_id` добавляется к событиям в сеансе расширенных событий. Если необходима дополнительная помощь в диагностике, то можно включить отслеживание доступа к данным и повторно выполнить команду соединения, а затем отследить в поле `ClientConnectionID` в трассировке доступа к данным операцию, завершившуюся ошибкой.  
  
 Если вы используете ODBC в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственном клиенте и соединение выполняется, можно получить идентификатор подключения клиента с помощью `SQL_COPT_SS_CLIENT_CONNECTION_ID` атрибута с [SQLGetConnectAttr](../../native-client-odbc-api/sqlgetconnectattr.md).  
  
 Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] также отправляет идентификатор активности конкретного потока. Идентификатор активности регистрируется в сеансах расширенных событий, если сеанс запущен со включенным параметром TRACK_CAUSAILITY. Если возникли проблемы производительности, связанные с активным соединением, то можно получить идентификатор активности из трассировки доступа клиента к данным (поле `ActivityID`) и найти идентификатор активности в выходных данных расширенных событий. Идентификатор активности в расширенном событии — это 16-байтовый идентификатор GUID (не совпадающий с идентификатором GUID подключения клиента), к которому добавлен четырехбайтовый номер последовательности. Номер последовательности представляет порядок запроса в потоке и указывает относительный порядок пакетных инструкций и инструкций RPC для данного потока. Идентификатор `ActivityID` также может отправляться для пакетных инструкций SQL и запросов RPC, если отслеживание доступа к данным включено, а 18-й бит слова конфигурации отслеживания доступа к данным установлен.  
  
 В следующем образце код [!INCLUDE[tsql](../../../includes/tsql-md.md)] служит для запуска сеанса расширенных событий, который будет сохраняться в кольцевом буфере и регистрировать идентификаторы активности, отправляемые с клиента при выполнении операций RPC и пакетных операций.  
  
```  
create event session MySession on server   
add event connectivity_ring_buffer_recorded,   
add event sql_statement_starting (action (client_connection_id)),   
add event sql_statement_completed (action (client_connection_id)),   
add event rpc_starting (action (client_connection_id)),   
add event rpc_completed (action (client_connection_id))  
add target ring_buffer with (track_causality=on)  
  
```  
  
## <a name="control-file"></a>Управляющий файл  
 В [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]управляющий файл собственного клиента SQL Server (ctrl.guid.snac11) содержит следующие данные:  
  
```  
{8B98D3F2-3CC6-0B9C-6651-9649CCE5C752}  0x00000000  0   MSDADIAG.ETW  
{2DA81B52-908E-7DB6-EF81-76856BB47C4F}  0xFFFFFFFF  0   SQLNCLI11.1  
```  
  
## <a name="mof-file"></a>MOF-файл  
 В [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]MOF-файл собственного клиента SQL Server содержит следующие данные:  
  
```  
#pragma classflags("forceupdate")  
#pragma namespace ("\\\\.\\Root\\WMI")  
  
/////////////////////////////////////////////////////////////////////////////  
//  
//  MSDADIAG.ETW  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW"),  
 Guid("{8B98D3F2-3CC6-0B9C-6651-9649CCE5C752}"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW : EventTrace  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW"),  
 Guid("{8B98D3F3-3CC6-0B9C-6651-9649CCE5C752}"),  
 DisplayName("msdadiag"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW_Trace : Bid2Etw_MSDADIAG_ETW  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW formatted output (A)"),  
 EventType(17),  
 EventTypeName("TextA"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW_Trace_TextA : Bid2Etw_MSDADIAG_ETW_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringA"),  
     extension("RString"),  
     read  
    ]  
    object msgStr;  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW formatted output (W)"),  
 EventType(18),  
 EventTypeName("TextW"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW_Trace_TextW : Bid2Etw_MSDADIAG_ETW_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringW"),  
     extension("RWString"),  
     read  
    ]  
    object msgStr;  
};  
  
/////////////////////////////////////////////////////////////////////////////  
//  
//  SQLNCLI11.1  
  
[  
 dynamic: ToInstance,  
 Description("SQLNCLI11.1"),  
 Guid("{2DA81B52-908E-7DB6-EF81-76856BB47C4F}"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_SQLNCLI11_1 : EventTrace  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("SQLNCLI11.1"),  
 Guid("{2DA81B53-908E-7DB6-EF81-76856BB47C4F}"),  
 DisplayName("SQLNCLI11.1"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_SQLNCLI11_1_Trace : Bid2Etw_SQLNCLI11_1  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("SQLNCLI11.1 formatted output (A)"),  
 EventType(17),  
 EventTypeName("TextA"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_SQLNCLI11_1_Trace_TextA : Bid2Etw_SQLNCLI11_1_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringA"),  
     extension("RString"),  
     read  
    ]  
    object msgStr;  
};  
  
[  
 dynamic: ToInstance,  
 Description("SQLNCLI11.1 formatted output (W)"),  
 EventType(18),  
 EventTypeName("TextW"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_SQLNCLI11_1_Trace_TextW : Bid2Etw_SQLNCLI11_1_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringW"),  
     extension("RWString"),  
     read  
    ]  
    object msgStr;  
};  
```  
  
## <a name="see-also"></a>См. также  
 [Обработка ошибок и сообщений](../../native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
