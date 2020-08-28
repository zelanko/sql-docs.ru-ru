---
description: Поставщик OLE DB Майкрософт для службы Microsoft Active Directory
title: Поставщик OLE DB Майкрософт для службы Microsoft Active Directory | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADSI provider [ADO]
- Active Directory Service Interfaces provider [ADO]
- providers [ADO], OLE DB provider for Active Directory service
- OLE DB provider for Active Directory service [ADO]
ms.assetid: f9e81452-5675-4cfc-9949-cfbd2fe57534
author: rothja
ms.author: jroth
ms.openlocfilehash: 08d945b101ac91300793920e3e01ea0a9619b372
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991055"
---
# <a name="microsoft-ole-db-provider-for-microsoft-active-directory-service"></a>Поставщик OLE DB Майкрософт для службы Microsoft Active Directory
Поставщик интерфейсов служб Active Directory (ADSI) позволяет ADO подключаться к разнородным службам каталогов через ADSI. Это дает приложениям ADO доступ только для чтения к службам каталогов Microsoft Windows NT 4,0 и Microsoft Windows 2000 в дополнение к любым LDAP-совместимым службам каталогов и службами каталогов Novell. Интерфейсы ADSI основаны на модели поставщика, поэтому при наличии нового поставщика, предоставляющего доступ к другому каталогу, приложение ADO будет иметь доступ к нему без проблем. Поставщик ADSI бесплатен и поддерживает Юникод.  
  
## <a name="connection-string-parameters"></a>Параметры строки соединения  
 Чтобы подключиться к этому поставщику, задайте для аргумента **поставщика** свойства [ConnectionString](../../reference/ado-api/connectionstring-property-ado.md) следующее значение:  
  
```vb
ADSDSOObject  
```  
  
 При чтении свойства [поставщика](../../reference/ado-api/provider-property-ado.md) также будет возвращена эта строка.  
  
## <a name="typical-connection-string"></a>Типичная строка подключения  
 Типичная строка подключения для этого поставщика выглядит следующим образом:  
  
```vb
"Provider=ADSDSOObject;User ID=MyUserID;Password=MyPassword;"  
```  
  
 Строка состоит из следующих ключевых слов.  
  
|Ключевое слово|Описание|  
|-------------|-----------------|  
|**Поставщик**|Указывает поставщика OLE DB для службы Active Directory.|  
|**Идентификатор пользователя**|Указывает имя пользователя. Если это ключевое слово опущено, используется текущий вход.|  
|**Пароль**|Указывает пароль пользователя. Значение, если ключевое слово пропущено. Затем используется текущий вход в систему.|  
  
> [!NOTE]
>  При подключении к поставщику источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = Yes** или **Integrated Security = SSPI** вместо сведений об идентификаторе пользователя и пароле в строке подключения.  
  
## <a name="command-text"></a>Текст команды  
 Поставщик в следующем синтаксисе распознает строку текста команды из четырех частей:  
  
```vb
"Root; Filter; Attributes[; Scope]"  
```  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Корневой*|Указывает **путь** к объекту, с которого начинается поиск (то есть корневой элемент поиска).|  
|*Filter*|Указывает фильтр поиска в формате RFC 1960.|  
|*Атрибуты*|Указывает разделенный запятыми список атрибутов, которые должны быть возвращены.|  
|*Область*|Необязательный элемент. **Строка** , указывающая область поиска. Может применяться один из перечисленных ниже типов.<br /><br /> -Base — Поиск только базового объекта (корень поиска).<br />-Одноуровневой — Поиск только на одном уровне.<br />-Subtree — Поиск по всему поддереву.|  
  
 Пример:  
  
```vb
"<LDAP://DC=ArcadiaBay,DC=COM>;(objectClass=*);sn, givenName; subtree"  
```  
  
 Поставщик также поддерживает SQL SELECT для текста команды. Пример:  
  
```vb
"SELECT title, telephoneNumber From 'LDAP://DC=Microsoft, DC=COM' WHERE   
objectClass='user' AND objectCategory='Person'"  
```  
  
## <a name="remarks"></a>Remarks  
 Поставщик не принимает вызовы хранимых процедур или простые имена таблиц (например, свойство [CommandType](../../reference/ado-api/commandtype-property-ado.md) всегда будет **адкмдтекст**). Более подробное описание элементов текста команды см. в документации по интерфейсам службы Active Directory.  
  
## <a name="recordset-behavior"></a>Поведение набора записей  
 В следующих таблицах перечислены функции, доступные в объекте [набора записей](../../reference/ado-api/recordset-object-ado.md) , открытом с помощью этого поставщика. Доступен только статический тип курсора (**адопенстатик**).  
  
 Чтобы получить дополнительные сведения о поведении **набора записей** для конфигурации поставщика, выполните метод [поддерживает](../../reference/ado-api/supports-method.md) и перечислите коллекцию [свойств](../../reference/ado-api/properties-collection-ado.md) **набора записей** , чтобы определить, имеются ли связанные с поставщиком динамические свойства.  
  
 **Доступность стандартных свойств набора записей ADO:**  
  
|Свойство|Доступность|  
|--------------|------------------|  
|[Примеры absolutepage](../../reference/ado-api/absolutepage-property-ado.md)|чтение/запись|  
|[Примеры AbsolutePosition](../../reference/ado-api/absoluteposition-property-ado.md)|чтение/запись|  
|[ActiveConnection](../../reference/ado-api/activeconnection-property-ado.md)|Только для чтения|  
|[BOF](../../reference/ado-api/bof-eof-properties-ado.md)|Только для чтения|  
|[Закладка.](../../reference/ado-api/bookmark-property-ado.md)|чтение/запись|  
|[CacheSize](../../reference/ado-api/cachesize-property-ado.md)|чтение/запись|  
|[CursorLocation](../../reference/ado-api/cursorlocation-property-ado.md)|всегда **адусесервер**|  
|[Примеры CursorType](../../reference/ado-api/cursortype-property-ado.md)|всегда **адопенстатик**|  
|[EditMode](../../reference/ado-api/editmode-property.md)|всегда **адедитноне**|  
|[КОНЦА](../../reference/ado-api/bof-eof-properties-ado.md)|Только для чтения|  
|[Filter](../../reference/ado-api/filter-property.md)|чтение/запись|  
|[LockType](../../reference/ado-api/locktype-property-ado.md)|чтение/запись|  
|[MarshalOptions](../../reference/ado-api/marshaloptions-property-ado.md)|недоступно|  
|[MaxRecords](../../reference/ado-api/maxrecords-property-ado.md)|чтение/запись|  
|[PageCount](../../reference/ado-api/pagecount-property-ado.md)|Только для чтения|  
|[PageSize](../../reference/ado-api/pagesize-property-ado.md)|чтение/запись|  
|[RecordCount](../../reference/ado-api/recordcount-property-ado.md)|Только для чтения|  
|[Source](../../reference/ado-api/source-property-ado-recordset.md)|чтение/запись|  
|[Состояние](../../reference/ado-api/state-property-ado.md)|Только для чтения|  
|[Состояние](../../reference/ado-api/status-property-ado-recordset.md)|Только для чтения|  
  
 **Доступность стандартных методов набора записей ADO:**  
  
|Метод|Доступно?|  
|------------|----------------|  
|[Вызов](../../reference/ado-api/addnew-method-ado.md)|Нет|  
|[Отмена](../../reference/ado-api/cancel-method-ado.md)|Нет|  
|[CancelBatch](../../reference/ado-api/cancelbatch-method-ado.md)|Нет|  
|[CancelUpdate](../../reference/ado-api/cancelupdate-method-ado.md)|Нет|  
|[Клонировать](../../reference/ado-api/clone-method-ado.md)|Да|  
|[Закрыть](../../reference/ado-api/close-method-ado.md)|Да|  
|[Удаление](../../reference/ado-api/delete-method-ado-recordset.md)|Нет|  
|[GetRows](../../reference/ado-api/getrows-method-ado.md)|Да|  
|[Перемещение](../../reference/ado-api/move-method-ado.md)|Да|  
|[MoveFirst](../../reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Да|  
|[MoveLast](../../reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Да|  
|[MoveNext](../../reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Да|  
|[MovePrevious](../../reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Да|  
|[NextRecordset](../../reference/ado-api/nextrecordset-method-ado.md)|Да|  
|[Открыть](../../reference/ado-api/open-method-ado-recordset.md)|Да|  
|[Повтор](../../reference/ado-api/requery-method.md)|Да|  
|[Повторная синхронизация](../../reference/ado-api/resync-method.md)|Да|  
|[Поддерживает](../../reference/ado-api/supports-method.md)|Да|  
|[Обновление](../../reference/ado-api/update-method.md)|Нет|  
|[UpdateBatch](../../reference/ado-api/updatebatch-method.md)|Нет|  
  
 Дополнительные сведения о ADSI и особенностях поставщика см. в документации по интерфейсам Active Directory служб или на веб-странице ADSI.  
  
## <a name="see-also"></a>См. также  
 [Свойство CommandType (ADO)](../../reference/ado-api/commandtype-property-ado.md)   
 [Свойство ConnectionString (ADO)](../../reference/ado-api/connectionstring-property-ado.md)   
 [Коллекция Properties (ADO)](../../reference/ado-api/properties-collection-ado.md)   
 [Свойство Provider (ADO)](../../reference/ado-api/provider-property-ado.md)   
 [Объект Recordset (ADO)](../../reference/ado-api/recordset-object-ado.md)   
 [Метод Supports](../../reference/ado-api/supports-method.md)