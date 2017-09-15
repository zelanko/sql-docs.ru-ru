---
title: "Написание собственного настраиваемого обработчика | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataFactory handler in RDS [ADO]
- customized handler in RDS [ADO]
ms.assetid: d447712a-e123-47b5-a3a4-5d366cfe8d72
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 445f0d8d7a870ceda6cf4028b0cebe9264ed8358
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="writing-your-own-customized-handler"></a>Написание собственного настраиваемого обработчика
Вы можете написать собственный обработчик, если вы являетесь администратором сервера IIS, желающему Поддержка служб удаленных рабочих СТОЛОВ, по умолчанию, но больший контроль над запросы пользователей и права доступа.  
  
 MSDFMAP. Реализует обработчик **IDataFactoryHandler** интерфейса.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="idatafactoryhandler-interface"></a>Интерфейс IDataFactoryHandler  
 Этот интерфейс содержит два метода **GetRecordset** и **повторное соединение**. Оба метода требуют [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойству присвоить значение **adUseClient**.  
  
 Оба метода принимают аргументы, которые отображаются после первой запятой в «**обработчик =**«ключевое слово. Например `"Handler=progid,arg1,arg2;"` передает строку аргумента `"arg1,arg2"`, и `"Handler=progid"` будет передавать аргумент null.  
  
## <a name="getrecordset-method"></a>Метод GetRecordset  
 Этот метод запрашивает источник данных и создает новую [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта, используя предоставленные аргументы. **Записей** должен открываться с **adLockBatchOptimistic** и не должен быть открыт асинхронно.  
  
### <a name="arguments"></a>Аргументы  
 ***conn*** строку подключения.  
  
 ***args*** аргументы для обработчика.  
  
 ***запрос*** текст команды для выполнения запроса.  
  
 ***ppRS*** указатель где **записей** должны быть возвращены.  
  
## <a name="reconnect-method"></a>Метод повторного подключения  
 Этот метод обновляет источник данных. Он создает новую [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта и присоединяет данного **записей**.  
  
### <a name="arguments"></a>Аргументы  
 ***conn*** строку подключения.  
  
 ***args*** аргументы для обработчика.  
  
 ***pRS*** A **записей** объекта.  
  
## <a name="msdfhdlidl"></a>msdfhdl.IDL  
 Это определение интерфейса для **IDataFactoryHandler** , которая отображается в **msdfhdl.idl** файла.  
  
```  
[  
  uuid(D80DE8B3-0001-11d1-91E6-00C04FBBBFB3),  
  version(1.0)  
]  
library MSDFHDL  
{  
    importlib("stdole32.tlb");  
    importlib("stdole2.tlb");  
  
    // TLib : Microsoft ActiveX Data Objects 2.0 Library  
    // {00000200-0000-0010-8000-00AA006D2EA4}  
    #ifdef IMPLIB  
    importlib("implib\\x86\\release\\ado\\msado15.dll");  
    #else  
    importlib("msado20.dll");  
    #endif  
  
    [  
      odl,  
      uuid(D80DE8B5-0001-11d1-91E6-00C04FBBBFB3),  
      version(1.0)  
    ]  
    interface IDataFactoryHandler : IUnknown  
    {  
HRESULT _stdcall GetRecordset(  
      [in] BSTR conn,  
      [in] BSTR args,  
      [in] BSTR query,  
      [out, retval] _Recordset **ppRS);  
  
// DataFactory will use the ActiveConnection property  
// on the Recordset after calling Reconnect.  
   HRESULT _stdcall Reconnect(  
      [in] BSTR conn,  
      [in] BSTR args,  
      [in] _Recordset *pRS);  
    };  
};  
```  
  
## <a name="see-also"></a>См. также:  
 [Файл настроек присоединения раздела](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Раздел журналы настройки файла](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [Раздел SQL настройки файла](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Раздел UserList настройки файла](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Настройка DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Параметры клиента](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Общие сведения о файле настроек](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)



