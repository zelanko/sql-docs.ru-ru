---
title: Интерфейс IMDEmbedded | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 9dba8c68-4bef-4c2b-815c-c286f1a1939b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 83e46e9b62359623093415ca456ecadd72f847cd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62757780"
---
# <a name="imdembedded-interface"></a>Интерфейс IMDEmbedded
  Интерфейс IMDEmbedded является открытым и служит для управления внедренной базой данных PowerPivot или шаблоном базы данных. Этот интерфейс наследует интерфейс `IPersistStream`. Этот интерфейс позволяет выполнить следующие операции:  
  
-   Получить идентификатор внедренного потока в документе-контейнере.  
  
-   Задать URL-адрес содержащего документа.  
  
-   Задать флаг, указывающий, находится ли внедряющее приложение в размещенной среде.  
  
-   Задать путь к временным файлам, используемым внедряющим приложением.  
  
-   Отменить текущую внедренную операцию.  
  
-   Получить прогнозируемый размер в байтах потока для сохранения внедренного объекта. Наследуется от `IPersistStream`.  
  
-   Проверить, изменилась ли внедренная база данных со времени ее последнего сохранения. Наследуется от `IPersistStream`.  
  
-   Загрузить внедренную базу данных в локальную или внутрипроцессную подсистему. Наследуется от `IPersistStream`.  
  
-   Сохранить локальную или внутрипроцессную базу данных во внедренном потоке в документе-контейнере. Наследуется от `IPersistStream`.  
  
## <a name="reference"></a>Справочник  
 В следующей справочной документации `IMDEmbedded` описывается интерфейс, представленный в файле заголовка **мсмд. h** .  
  
### <a name="source-file-pxoembeddeddataidl"></a>Исходный файл: PXOEmbeddedData.idl  
  
```  
[  
  local,                            
  object,                           
  uuid(6B6691CF-5453-41c2-ADD9-4F320B7FD421),                       
  pointer_default(unique)           
]  
interface IMDEmbeddedData : IPersistStream  
{  
 [id(1), helpstring("Set flag indicating if the application is in a hosted environment")]   
 HRESULT SetHosted(  
  [in] BOOL in_fIsHosted);  
  
 [id(2), helpstring("Set the URL for the document containing the embedded stream")]   
 HRESULT SetContainerURL(  
  [in] BSTR in_bstrURL);  
  
 [id(3), helpstring("Get identifier used to look up embedded stream in container document")]   
 HRESULT GetStreamIdentifier(  
  [out, retval] BSTR* out_pbstrStreamId);  
  
 [id(4), helpstring("Set the path used by the embedding application for temporary files")]   
 HRESULT SetTempDirPath(  
  [in]  BSTR in_bstrPath);  
  
 [id(5), helpstring("Cancel the current operation")]   
 HRESULT Cancel();  
};  
```  
  
### <a name="imdembeddeddatagetstreamidentifier"></a>IMDEmbeddedData::GetStreamIdentifier  
  
```  
HRESULT GetStreamIdentifier (  
    [out, retval] BSTR * out_pbstrStreamId  
    )  
```  
  
#### <a name="description"></a>Description  
 Возвращает идентификатор, используемый ведущим приложением для внедренного потока в документе-контейнере.  
  
#### <a name="parameters"></a>Параметры  
 *out_pbstrStreamId*  
 Указывает местоположение идентификатора потока.  
  
#### <a name="return-value"></a>Возвращаемое значение  
 `S_OK`  
 Идентификатор потока был успешно возвращен.  
  
 `S_FALSE`  
 Идентификатор потока отсутствует.  
  
 `E_FAIL`  
 При получении доступа к идентификатору потока произошла ошибка.  
  
#### <a name="remarks"></a>Remarks  
 Чтобы проверить, содержит ли текущее соединение внедренную базу данных, пользователь должен проверить значение свойства DBPROP_MSMD_EMBEDDED_DATA, являющееся одним из свойств соединения OLE DB.  
  
 Возможные значения для DBPROP_MSMD_EMBEDDED_DATA.  
  
|Имя|Значение|Определение|  
|----------|-----------|----------------|  
|DBPROPVAL_EMBED_NONE|0x00|Доступная внедренная база данных отсутствует|  
|DBPROPVAL_EMBED_EMBEDDED|0x01|Текущее приложение содержит внедренную базу данных|  
|DBPROPVAL_EMBED_LINKED|0x02|Внедренная база данных размещена в удаленном приложении (т. е. на сервере SharePoint)|  
  
#### <a name="source"></a>Источник  
  
```  
[id(1), helpstring("Get identifier used to look up embedded stream in container document")]   
 HRESULT GetStreamIdentifier(  
  [out, retval] BSTR* out_pbstrStreamId);  
```  
  
### <a name="imdembeddeddatasetcontainerurl"></a>IMDEmbeddedData::SetContainerURL  
  
```  
HRESULT SetContainerURL (  
    [in] BSTR in_bstrURL  
    )  
```  
  
#### <a name="description"></a>Description  
 Задает URL-адрес для файла, содержащего внедренный поток.  
  
#### <a name="parameters"></a>Параметры  
 *in_bstrURL*  
 Указывает URL-адрес для содержащего документа.  
  
#### <a name="return-value"></a>Возвращаемое значение  
 `S_OK`  
 URL-адрес контейнера был успешно задан.  
  
 `E_FAIL`  
 При задании URL-адреса контейнера произошла ошибка.  
  
#### <a name="source"></a>Источник  
  
```  
[id(2), helpstring("Set the URL for the document containing the embedded stream")]   
 HRESULT SetContainerURL(  
  [in] BSTR in_bstrURL);  
```  
  
### <a name="imdembeddeddatasethosted"></a>IMDEmbeddedData::SetHosted  
  
```  
HRESULT SetHosted (  
    [in] BOOL in_fIsHosted  
    )  
```  
  
#### <a name="description"></a>Description  
 Задать флаг, указывающий, находится ли внедряющее приложение в размещенной среде.  
  
#### <a name="parameters"></a>Параметры  
 *in_ftHosted*  
 TRUE, если вызывающий объект находится в приложении, размещенном в службе (например IIS).  
  
#### <a name="return-value"></a>Возвращаемое значение  
 `S_OK`  
 Флаг был успешно задан.  
  
 `E_FAIL`  
 При задании флага произошла ошибка.  
  
#### <a name="source"></a>Источник  
  
```  
[id(5), helpstring("Set flag indicating if the application is in a hosted environment")]   
 HRESULT SetHosted(  
  [in]  BOOL in_fIsHosted);  
```  
  
### <a name="imdembeddeddatasettempdirpath"></a>IMDEmbeddedData::SetTempDirPath  
  
```  
HRESULT SetTempDirPath (  
    [in] BSTR in_bstrPath  
    )  
```  
  
#### <a name="description"></a>Description  
 Задать путь к временным файлам, используемым внедряющим приложением.  
  
#### <a name="parameters"></a>Параметры  
 *in_bstrPath*  
 Путь, используемый ведущим приложением для временных файлов.  
  
#### <a name="return-value"></a>Возвращаемое значение  
 `S_OK`  
 Каталог временного файла был успешно задан.  
  
 `E_FAIL`  
 При задании пути произошла ошибка.  
  
#### <a name="source"></a>Источник  
  
```  
[id(4), helpstring("Set the path used by the host application for temporary files")]   
 HRESULT SetTempDirPath(  
  [in]  BSTR in_bstrPath);  
```  
  
### <a name="imdembeddeddatacancel"></a>IMDEmbeddedData::Cancel  
  
```  
HRESULT Cancel ( void )  
```  
  
#### <a name="description"></a>Description  
 Отменяет текущую операцию внедренной базы данных  
  
#### <a name="parameters"></a>Параметры  
 Нет.  
  
#### <a name="return-value"></a>Возвращаемое значение  
 `S_OK`  
 Операция была успешно отменена.  
  
 `DB_E_CANTCANCEL`  
 В настоящее время не выполняется ни одна операция, которую можно отменить.  
  
 `E_FAIL`  
 При отмене внедренной операции произошла ошибка.  
  
#### <a name="source"></a>Источник  
  
```  
[id(5), helpstring("Cancel the current operation")]   
 HRESULT Cancel();  
```  
  
### <a name="imdembeddeddatagetsizemax-ipersiststreamgetsizemax"></a>IMDEmbeddedData::GetSizeMax (IPersistStream::GetSizeMax)  
  
```  
HRESULT GetSizeMax (  
    [out] ULARGE_INTEGER * out_pcbSize  
    )  
```  
  
#### <a name="description"></a>Description  
 Возвращает прогнозируемый размер в байтах потока для сохранения внедренного объекта. Наследуется от `IPersistStream`.  
  
#### <a name="parameters"></a>Параметры  
 *in_bstrPath*  
 Прогнозируемый размер в байтах образа внедренной базы данных.  
  
#### <a name="return-value"></a>Возвращаемое значение  
 `S_OK`  
 Размер был успешно получен.  
  
 `E_FAIL`  
 При получении размера произошла ошибка.  
  
### <a name="imdembeddeddataisdirty-ipersiststreamisdirty"></a>IMDEmbeddedData::IsDirty (IPersistStream::IsDirty)  
  
```  
HRESULT IsDirty ( void )  
```  
  
#### <a name="description"></a>Description  
 Проверяет, изменилась ли внедренная база данных со времени последнего сохранения. Наследуется от `IPersistStream`.  
  
#### <a name="parameters"></a>Параметры  
 none  
  
#### <a name="return-values"></a>Возвращаемые значения  
 `S_OK`  
 База данных изменилась со времени последнего сохранения.  
  
 `S_FALSE`  
 База данных не изменилась со времени последнего сохранения.  
  
 `E_FAIL`  
 При получении состояния базы данных произошла ошибка.  
  
### <a name="imdembeddeddataload-ipersiststreamload"></a>IMDEmbeddedData::Load (IPersistStream::Load)  
  
```  
HRESULT Load (   
    [in] IStream * in_pStm   
    )  
```  
  
#### <a name="description"></a>Description  
 Загружает внедренную базу данных в локальную или внутрипроцессную подсистему. Наследуется от `IPersistStream`.  
  
#### <a name="parameters"></a>Параметры  
 *in_pStm*  
 Указатель на интерфейс потока, из которого должна быть загружена внедренная база данных.  
  
#### <a name="return-values"></a>Возвращаемые значения  
 `S_OK`  
 База данных была успешно загружена.  
  
 `E_OUTOFMEMORY`  
 Недостаточно памяти для загрузки базы данных.  
  
 `E_FAIL`  
 При загрузке базы данных произошла ошибка, отличная от `E_OUTOFMEMORY`.  
  
### <a name="imdembeddeddatasave-ipersiststreamsave"></a>IMDEmbeddedData::Save (IPersistStream::Save)  
  
```  
HRESULT Save (   
    [in] IStream * in_pStm,  
    [in] BOOL in_fClearDirty  
    )  
```  
  
#### <a name="description"></a>Description  
 Сохраняет локальную или внутрипроцессную базу данных во внедренном потоке в документе-контейнере. Наследуется от `IPersistStream`.  
  
#### <a name="parameters"></a>Параметры  
 *in_pStm*  
 Указатель на интерфейс потока, в который должна быть сохранена внедренная база данных.  
  
 *in_fClearDirty*  
 Флаг, который указывает, должен ли флаг «грязных» данных быть очищен после этой операции.  
  
#### <a name="return-values"></a>Возвращаемые значения  
 `S_OK`  
 База данных была успешно сохранена.  
  
 `STG_E_CANTSAVE`  
 Во время сохранения базы данных произошла ошибка, отличная от `STG_E_MEDIUMFULL`.  
  
 `STG_E_MEDIUMFULL`  
 База данных не могла быть сохранена, поскольку на запоминающем устройстве не осталось места.  
  
  
