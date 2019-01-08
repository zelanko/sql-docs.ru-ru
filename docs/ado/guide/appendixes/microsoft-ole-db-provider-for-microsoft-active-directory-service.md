---
title: Поставщик Microsoft OLE DB для службы Microsoft Active Directory | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 25a076118df9f85ff2449c35dc0273db8a499fac
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52538159"
---
# <a name="microsoft-ole-db-provider-for-microsoft-active-directory-service"></a>Поставщик Microsoft OLE DB для службы Microsoft Active Directory
Поставщик интерфейсы служб Active Directory (ADSI) разрешает ADO для подключения к службам разнородных directory через ADSI. Это дает приложения ADO доступ только для чтения в каталоге служб Microsoft Windows NT 4.0 и Microsoft Windows 2000, а также все службы, совместимой с LDAP directory и служб каталога Novell. Сам интерфейс ADSI основан на модели поставщика, таким образом, если имеется новый предоставить доступ поставщика в другой каталог, приложения ADO будет получить к ним доступ без проблем. Поставщик ADSI является свободнопотоковым и Юникод.  
  
## <a name="connection-string-parameters"></a>Параметры строки соединения  
 Чтобы подключиться к этим поставщиком, задайте **поставщика** аргумент [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) следующие свойства:  
  
```vb
ADSDSOObject  
```  
  
 Чтение [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) свойство возвратит также эту строку.  
  
## <a name="typical-connection-string"></a>Типичная строка подключения  
 Строка соединения для данного поставщика выглядит следующим образом:  
  
```vb
"Provider=ADSDSOObject;User ID=MyUserID;Password=MyPassword;"  
```  
  
 Строка состоит из следующих ключевых слов.  
  
|Ключевое слово|Описание|  
|-------------|-----------------|  
|**Поставщик**|Указывает поставщика OLE DB для службы Active Directory.|  
|**Идентификатор пользователя**|Указывает имя пользователя. Если это ключевое слово указан, используется текущее имя входа.|  
|**Пароль**|Указывает пароль пользователя. Если это ключевое слово указан. Затем используется текущее имя входа.|  
  
> [!NOTE]
>  Если вы подключаетесь к поставщик источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = yes** или **Integrated Security = SSPI** вместо идентификатора пользователя и пароля сведения в строке подключения.  
  
## <a name="command-text"></a>Текст команды  
 Команда из четырех частей текстовую строку распознается поставщиком в следующий синтаксис:  
  
```vb
"Root; Filter; Attributes[; Scope]"  
```  
  
|Значение|Описание|  
|-----------|-----------------|  
|*Root*|Указывает **ADsPath** объект, из которого следует начать поиск (то есть корень поиска).|  
|*Фильтр*|Указывает фильтр поиска в формате RFC 1960 года.|  
|*Атрибуты*|Указывает список атрибутов, возвращаемых с разделителями запятыми.|  
|*Область*|Необязательный. Объект **строка** , определяющее область поиска. Возможен один из следующих вариантов.<br /><br /> -Base - поиск только базового объекта (корень поиска).<br />-Одноуровневой - только один уровень поиска.<br />-Поддерево - поиска просматривается все поддерево.|  
  
 Пример:  
  
```vb
"<LDAP://DC=ArcadiaBay,DC=COM>;(objectClass=*);sn, givenName; subtree"  
```  
  
 Поставщик также поддерживает SQL SELECT для текста команды. Пример:  
  
```vb
"SELECT title, telephoneNumber From 'LDAP://DC=Microsoft, DC=COM' WHERE   
objectClass='user' AND objectCategory='Person'"  
```  
  
## <a name="remarks"></a>Примечания  
 Поставщик не поддерживает вызовы хранимых процедур и простую таблицу имена (например, [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) свойство будет всегда **adCmdText**). См. в документации интерфейсы служб Active Directory, более подробное описание элементов текста команды.  
  
## <a name="recordset-behavior"></a>Поведение набора записей  
 В следующих таблицах перечислены функции, доступные при [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объект открыт с помощью этого поставщика. Только тип статического курсора (**adOpenStatic**) доступен.  
  
 Дополнительные сведения о **записей** поведение поставщика конфигурации, запустите [поддерживает](../../../ado/reference/ado-api/supports-method.md) метод и перечисление [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекцию  **Набор записей** чтобы определить, присутствует ли динамические свойства от поставщика.  
  
 **Доступность стандартных свойств набора записей ADO.**  
  
|Свойство|Доступность|  
|--------------|------------------|  
|[Примеры AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|чтение/запись|  
|[Примеры AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|чтение/запись|  
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|только для чтения|  
|[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|только для чтения|  
|[Закладка](../../../ado/reference/ado-api/bookmark-property-ado.md)|чтение/запись|  
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|чтение/запись|  
|[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|всегда **adUseServer**|  
|[Примеры CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|всегда **adOpenStatic**|  
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|всегда **как таковые**|  
|[КОНЕЦ ФАЙЛА](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|только для чтения|  
|[Фильтр](../../../ado/reference/ado-api/filter-property.md)|чтение/запись|  
|[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)|чтение/запись|  
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|недоступно|  
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|чтение/запись|  
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|только для чтения|  
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|чтение/запись|  
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|только для чтения|  
|[Source](../../../ado/reference/ado-api/source-property-ado-recordset.md)|чтение/запись|  
|[Состояние](../../../ado/reference/ado-api/state-property-ado.md)|только для чтения|  
|[Состояние](../../../ado/reference/ado-api/status-property-ado-recordset.md)|только для чтения|  
  
 **Доступность стандартных методов набора записей ADO.**  
  
|Метод|Доступны?|  
|------------|----------------|  
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|Нет|  
|[Отмена](../../../ado/reference/ado-api/cancel-method-ado.md)|Нет|  
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|Нет|  
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|Нет|  
|[Клон](../../../ado/reference/ado-api/clone-method-ado.md)|Да|  
|[Закрыть](../../../ado/reference/ado-api/close-method-ado.md)|Да|  
|[Удаление](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|Нет|  
|[Получение строк](../../../ado/reference/ado-api/getrows-method-ado.md)|Да|  
|[Переместить](../../../ado/reference/ado-api/move-method-ado.md)|Да|  
|[MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Да|  
|[MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Да|  
|[MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Да|  
|[MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Да|  
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)|Да|  
|[Открытие](../../../ado/reference/ado-api/open-method-ado-recordset.md)|Да|  
|[Requery](../../../ado/reference/ado-api/requery-method.md)|Да|  
|[Повторная синхронизация](../../../ado/reference/ado-api/resync-method.md)|Да|  
|[Поддерживает](../../../ado/reference/ado-api/supports-method.md)|Да|  
|[Update](../../../ado/reference/ado-api/update-method.md)|Нет|  
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|Нет|  
  
 Дополнительные сведения об ADSI и особенности обеспечения поставщика см. в документации интерфейсы служб Active Directory или ADSI веб-странице.  
  
## <a name="see-also"></a>См. также  
 [Свойство CommandType (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md)   
 [Свойство ConnectionString (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Свойство Provider (ADO)](../../../ado/reference/ado-api/provider-property-ado.md)   
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Метод Supports](../../../ado/reference/ado-api/supports-method.md)
