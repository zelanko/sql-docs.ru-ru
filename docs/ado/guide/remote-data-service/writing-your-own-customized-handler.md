---
title: Написание собственного настраиваемого обработчика | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- DataFactory handler in RDS [ADO]
- customized handler in RDS [ADO]
ms.assetid: d447712a-e123-47b5-a3a4-5d366cfe8d72
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 58a380336d3b1abc99e00f1f4052cd24a8cc5988
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66699411"
---
# <a name="writing-your-own-customized-handler"></a>Создание собственного настраиваемого обработчика
Вы можете написать собственный обработчик, если вы являетесь администратором сервера IIS, желающего поддерживать служб удаленных рабочих СТОЛОВ, значение по умолчанию, но больший контроль над запросами пользователей и права доступа.  
  
 MSDFMAP. Реализует обработчик **IDataFactoryHandler** интерфейс.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="idatafactoryhandler-interface"></a>Интерфейс IDataFactoryHandler  
 Этот интерфейс содержит два метода **GetRecordset** и **повторное соединение**. Оба метода требуют [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойства задать значение **adUseClient**.  
  
 Оба метода используют аргументы, которые отображаются после первой запятой в "**обработчик =**" ключевое слово. Например `"Handler=progid,arg1,arg2;"` будет передана строка аргумента из `"arg1,arg2"`, и `"Handler=progid"` передаст аргументом null.  
  
## <a name="getrecordset-method"></a>Метод GetRecordset  
 Этот метод отправляет запросы к источнику данных и создает новый [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объект по указанным аргументам. **Записей** должен открываться с **adLockBatchOptimistic** и не должен быть открыт асинхронно.  
  
### <a name="arguments"></a>Аргументы  
 ***conn*** строку подключения.  
  
 ***args*** аргументы для обработчика.  
  
 ***запрос*** текст команды для выполнения запроса.  
  
 ***ppRS*** указатель где **записей** должны быть возвращены.  
  
## <a name="reconnect-method"></a>Повторное подключение, метод  
 Этот метод обновляет источник данных. Он создает новую [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта и подключает к заданной **записей**.  
  
### <a name="arguments"></a>Аргументы  
 ***conn*** строку подключения.  
  
 ***args*** аргументы для обработчика.  
  
 ***запросы на Вытягивание*** объект **записей** объекта.  
  
## <a name="msdfhdlidl"></a>msdfhdl.idl  
 Это определение интерфейса **IDataFactoryHandler** , отображаемый в **msdfhdl.idl** файла.  
  
```cpp
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
  
## <a name="see-also"></a>См. также  
 [Настройка раздела подключения файла](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Настройка раздела журналов файла](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [Настройка раздела SQL файла](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Настройка раздела UserList файла](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Настройка DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Необходимые параметры клиентов](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Общие сведения о файле настроек](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)


