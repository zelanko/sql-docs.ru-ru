---
title: "Свойство ConnectionString (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Connection15::ConnectionString
helpviewer_keywords:
- ConnectionString property [ADO]
ms.assetid: 3be75b75-4d36-4479-ab64-9a456869252a
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 34db69d25ff835de4f8c81d252c99017ae4acbb5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="connectionstring-property-ado"></a>Свойство ConnectionString (ADO)
Указывает сведения, используемые для установления соединения с источником данных.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** значение.  
  
## <a name="remarks"></a>Замечания  
 Используйте **ConnectionString** свойство, чтобы указать источник данных, передав подробную строку подключения с сериями *аргумент* *= значение* разделенных инструкций точка с запятой.  
  
 ADO поддерживает пять аргументов для **ConnectionString** свойство; другие аргументы проход непосредственно к поставщику без обработки с ADO. Поддержка ADO аргументы выглядят следующим образом.  
  
|Аргумент|Description|  
|--------------|-----------------|  
|*Поставщик =*|Задает имя поставщика, который используется для подключения.|  
|*Имя файла =*|Указывает имя файла поставщика (например, объект источника материализованных данных), содержащий сведения о подключении предустановки.|  
|*Удаленный поставщик =*|Задает имя поставщика, который используется при открытии клиентского соединения. (Удаленный канал передачи данных только.)|  
|*Удаленный сервер =*|Задает имя пути сервера для использования при открытии клиентского соединения. (Удаленный канал передачи данных только.)|  
|*URL-АДРЕС =*|Указывает строку подключения, как абсолютный URL-адрес, идентифицирующий ресурса, например файла или каталога.|  
  
 После установки **ConnectionString** свойств и открыть [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта, поставщик может изменить содержимое свойства, например, путем сопоставления имен аргументов определяемых ADO для их эквиваленты для конкретного поставщика.  
  
 **ConnectionString** свойство автоматически наследует значение, используемое для *ConnectionString* аргумент [откройте](../../../ado/reference/ado-api/open-method-ado-connection.md) метод, поэтому переопределение текущего  **ConnectionString** во время **откройте** вызова метода.  
  
 Поскольку *имя файла* аргумент указывает ADO для загрузки связанного поставщика, невозможно передать оба *поставщика* и *имя файла* аргументы.  
  
 **ConnectionString** свойство является чтение и запись, когда подключение закрыто, только для чтения при открытом.  
  
 Повторяющиеся значения аргумента в **ConnectionString** свойства игнорируются. Используется последний экземпляр любого из аргументов.  
  
> [!NOTE]
>  **Удаленное использование службы данных** при использовании на стороне клиента **подключения** объекта, **ConnectionString** свойство может содержать только *удаленного поставщика*и *удаленного сервера* параметров.  
  
 В следующей таблице перечислены ADO поставщика по умолчанию для каждой операционной системы Windows:  
  
|Поставщик ADO по умолчанию|Операционная система Windows|  
|--------------------------|------------------------------|  
|MSDASQL<br /><br /> (Чтобы повысить удобочитаемость исходного кода, явно укажите имя поставщика в строке подключения.)|Windows 2000 (32-разрядная версия)<br /><br /> Windows XP (32-разрядная версия)<br /><br /> Windows Server 2003 (32-разрядная версия)<br /><br /> Windows Vista (32-разрядная версия)<br /><br /> Пакет обновления 1 для Windows Vista или более поздней версии (32-разрядных и 64-разрядная)<br /><br /> Версии Windows после Windows Vista (32-разрядных и 64-разрядная)|  
|Значение по умолчанию отсутствует.<br /><br /> Когда приложение ADO работает в следующих операционных системах и явно не указан поставщик, ADO возвращает следующую ошибку: «ADODB. Подключение: не указан и не заданного по умолчанию поставщик»|Windows 2000 (64-разрядная версия)<br /><br /> Windows XP (64-разрядная версия)<br /><br /> Windows Server 2003 (64-разрядная версия)<br /><br /> Windows Vista (64-разрядная версия)|  
  
## <a name="applies-to"></a>Объект применения  
 [Объект соединения (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [ConnectionString, ConnectionTimeout и пример свойства состояния (Visual Basic)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString, ConnectionTimeout и пример свойства состояния (VC ++)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
 [Поставщики приложение A:](../../../ado/guide/appendixes/appendix-a-providers.md)

