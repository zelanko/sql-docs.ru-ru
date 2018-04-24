---
title: Метод ConvertToString (RDS) | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- ConvertToString method [ADO]
ms.assetid: b3f36bc8-6f69-49b0-83cd-2ccd3afebfbe
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ec84e0a0816ffab9246aaee4653507ee07dc3dab
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="converttostring-method-rds"></a>Метод ConvertToString (RDS)
Преобразует [записей](../../../ado/reference/ado-api/recordset-object-ado.md) MIME строку, которая представляет данные набора записей.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataFactory.ConvertToString(Recordset)  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataFactory*  
 Объектную переменную, которая представляет [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) объекта.  
  
 *Набор записей*  
 Объектную переменную, которая представляет **записей** объекта.  
  
## <a name="remarks"></a>Замечания  
 Файлы .asp использовать **ConvertToString** для внедрения **записей** в HTML-страницы, созданные на сервере, чтобы перенести его на клиентском компьютере.  
  
 **ConvertToString** сначала загружает **записей** курсора службой таблиц и создает поток в формате MIME.  
  
 На стороне клиента удаленной службы данных можно преобразовать строку MIME обратно в полностью функциональный **записей**. Она подходит для обработки менее 400 строк данных с не более 1024 байта ширины каждой строки. Не следует использовать его для потоковой передачи данных большого двоичного ОБЪЕКТА и большие результирующие наборы по протоколу HTTP. Сжатие не передачи выполняется в строке, очень большие наборы данных занять значительное время для транспорта по протоколу HTTP, по сравнению с оптимизированными для передачи tablegram формат определяются и развертываются с удаленной службы данных в качестве его формат собственного транспортного протокола.  
  
> [!NOTE]
>  Если вы используете Active Server Pages для внедрения результирующая строка MIME в HTML-страницей клиента, имейте в виду, что версиях VBScript, предшествующих версии 2.0 ограничение на размер строки 32 КБ. Если этот предел превышен, возвращается ошибка. Сохраните относительно небольшой области запроса при использовании внедрения MIME с помощью ASP-файлы. Чтобы устранить эту проблему, загрузите последнюю версию VBScript из технологий скрипта Windows веб-узла.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода ConvertToString (Visual Basic)](../../../ado/reference/ado-api/converttostring-method-example-vb.md)   
 [Пример метода ConvertToString (VBScript)](../../../ado/reference/rds-api/converttostring-method-example-vbscript.md)


