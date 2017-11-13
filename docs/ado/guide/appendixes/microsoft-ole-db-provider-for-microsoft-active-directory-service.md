---
title: "Поставщик Microsoft OLE DB для службы Microsoft Active Directory | Документы Microsoft"
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
- ADSI provider [ADO]
- Active Directory Service Interfaces provider [ADO]
- providers [ADO], OLE DB provider for Active Directory service
- OLE DB provider for Active Directory service [ADO]
ms.assetid: f9e81452-5675-4cfc-9949-cfbd2fe57534
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cc6946f6944cf37f85759847f2c8db852d120461
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="microsoft-ole-db-provider-for-microsoft-active-directory-service"></a>Поставщик Microsoft OLE DB для службы Microsoft Active Directory
Поставщик интерфейсы службы Active Directory (ADSI) позволяет ADO для подключения к службам каталогов разнородных через ADSI. Это дает приложения ADO доступ только для чтения в каталоге служб Microsoft Windows NT 4.0 и Microsoft Windows 2000, помимо любой совместимый с LDAP службы каталогов и Novell Directory Services. Сам интерфейс ADSI основан на модель поставщика, чтобы в случае нового обеспечивающий доступ поставщика в другой каталог приложения ADO будет получить к ним доступ без проблем. Поставщик является поставщиком ADSI свободнопоточный и Юникод.  
  
## <a name="connection-string-parameters"></a>Параметры строки соединения  
 Чтобы подключиться к этому поставщику, задайте **поставщика** аргумент [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) следующее:  
  
```  
ADSDSOObject  
```  
  
 Чтение [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) свойство возвратит также этой строки.  
  
## <a name="typical-connection-string"></a>Обычная строка соединения  
 Для данного поставщика строка соединения выглядит следующим образом:  
  
```  
"Provider=ADSDSOObject;User ID=MyUserID;Password=MyPassword;"  
```  
  
 Строка состоит из следующих ключевых слов.  
  
|Ключевое слово|Description|  
|-------------|-----------------|  
|**Поставщик**|Указывает поставщика OLE DB для службы каталогов Active Directory.|  
|**Идентификатор пользователя**|Указывает имя пользователя. Если это ключевое слово задан, используется текущая учетная запись.|  
|**Пароль**|Указывает пароль пользователя. Если это ключевое слово задан. Затем используется текущая учетная запись.|  
  
> [!NOTE]
>  При подключении к поставщик источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = yes** или **Integrated Security = SSPI** вместо идентификатора пользователя и пароля сведения в строке подключения.  
  
## <a name="command-text"></a>Текст команды  
 Строка текста команды из четырех частей распознается поставщиком используется следующий синтаксис:  
  
```  
"Root; Filter; Attributes[; Scope]"  
```  
  
|Значение|Description|  
|-----------|-----------------|  
|*Root*|Указывает **ADsPath** объект, из которого следует начинать поиск (то есть корневой поиска).|  
|*Filter*|Указывает фильтр поиска в формате RFC 1960.|  
|*Атрибуты*|Указывает список с разделителями запятыми атрибутов должны быть возвращены.|  
|*Область действия*|Необязательно. Объект **строка** , указывающий область поиска. Возможен один из следующих вариантов.<br /><br /> -Base — Поиск только базового объекта (корень поиска).<br />-OneLevel — Поиск только один уровень.<br />-Поддерево — Поиск всего поддерева.|  
  
 Например:  
  
```  
"<LDAP://DC=ArcadiaBay,DC=COM>;(objectClass=*);sn, givenName; subtree"  
```  
  
 Поставщик также поддерживает SQL SELECT в тексте команды. Например:  
  
```  
"SELECT title, telephoneNumber From 'LDAP://DC=Microsoft, DC=COM' WHERE   
objectClass='user' AND objectCategory='Person'"  
```  
  
## <a name="remarks"></a>Замечания  
 Поставщик не поддерживает вызовы хранимых процедур и имена простую таблицу (например, [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) всегда будет иметь свойство **adCmdText**). См. в документации интерфейсы служб Active Directory более полное описание элементов текста команды.  
  
## <a name="recordset-behavior"></a>Поведение набора записей  
 В следующих таблицах перечислены возможности, доступные в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объект открыт с помощью этого поставщика. Только тип статического курсора (**adOpenStatic**) доступен.  
  
 Дополнительные сведения о **записей** поведение конфигурации поставщика, запустите [поддерживает](../../../ado/reference/ado-api/supports-method.md) метод и перечисление [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекцию  **Набор записей** для определения того, присутствуют ли динамические свойства от поставщика.  
  
 **Доступность стандартных свойств набора записей ADO:**  
  
|Свойство|Доступность|  
|--------------|------------------|  
|[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|чтение/запись|  
|[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|чтение/запись|  
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|только для чтения|  
|[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|только для чтения|  
|[Закладка](../../../ado/reference/ado-api/bookmark-property-ado.md)|чтение/запись|  
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|чтение/запись|  
|[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|всегда **adUseServer**|  
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|всегда **adOpenStatic**|  
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|всегда **как таковые**|  
|[КОНЕЦ ФАЙЛА](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|только для чтения|  
|[Filter](../../../ado/reference/ado-api/filter-property.md)|чтение/запись|  
|[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)|чтение/запись|  
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|недоступно|  
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|чтение/запись|  
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|только для чтения|  
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|чтение/запись|  
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|только для чтения|  
|[Source](../../../ado/reference/ado-api/source-property-ado-recordset.md)|чтение/запись|  
|[Состояние](../../../ado/reference/ado-api/state-property-ado.md)|только для чтения|  
|[Состояние](../../../ado/reference/ado-api/status-property-ado-recordset.md)|только для чтения|  
  
 **Доступность стандартных методов набора записей ADO:**  
  
|Метод|Доступны?|  
|------------|----------------|  
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|Нет|  
|[Отмена](../../../ado/reference/ado-api/cancel-method-ado.md)|Нет|  
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|Нет|  
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|Нет|  
|[Клон](../../../ado/reference/ado-api/clone-method-ado.md)|Да|  
|[Закрыть](../../../ado/reference/ado-api/close-method-ado.md)|Да|  
|[Delete](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|Нет|  
|[Получение строк](../../../ado/reference/ado-api/getrows-method-ado.md)|Да|  
|[Переместить](../../../ado/reference/ado-api/move-method-ado.md)|Да|  
|[MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Да|  
|[MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Да|  
|[MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Да|  
|[MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Да|  
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)|Да|  
|[Открытие](../../../ado/reference/ado-api/open-method-ado-recordset.md)|Да|  
|[Повторный запрос](../../../ado/reference/ado-api/requery-method.md)|Да|  
|[Повторная синхронизация](../../../ado/reference/ado-api/resync-method.md)|Да|  
|[Поддерживает](../../../ado/reference/ado-api/supports-method.md)|Да|  
|[Update](../../../ado/reference/ado-api/update-method.md)|Нет|  
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|Нет|  
  
 Дополнительные сведения о ADSI и подробной информации о поставщике обратитесь к документации интерфейсы служб Active Directory или посетите ADSI веб-странице.  
  
## <a name="see-also"></a>См. также:  
 [Свойство CommandType (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md)   
 [Свойство ConnectionString (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md)   
 [Коллекция свойств (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Свойство поставщика (ADO)](../../../ado/reference/ado-api/provider-property-ado.md)   
 [Объект набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Поддерживает метод](../../../ado/reference/ado-api/supports-method.md)

