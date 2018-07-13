---
title: IRowsetFastLoad::Commit (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IRowsetFastLoad::Commit (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Commit method
ms.assetid: 19de9128-b91a-4626-847f-af721edaa24e
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 745282c1d1e8fa36c9d0a407ac32171304d05197
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37417173"
---
# <a name="irowsetfastloadcommit-ole-db"></a>IRowsetFastLoad::Commit (OLE DB)
  Обозначает конец пакета вставляемых строк и записывает эти строки в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Примеры, см. в разделе [массового копирования данных с помощью IRowsetFastLoad &#40;OLE DB&#41; ](irowsetfastload-ole-db.md) и [отправить данные больших двоичных ОБЪЕКТОВ SQL SERVER с помощью IROWSETFASTLOAD и ISEQUENTIALSTREAM &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT Commit(  
BOOL   
fDone  
);  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *fDone*[in]  
 Если значение равно FALSE, то набор строк сохраняет достоверность и может использоваться пользователем для дополнительной вставки строк. Если значение равно TRUE, то набор строк теряет достоверность и пользователь не может выполнять дальнейшую вставку.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 S_OK  
 Метод завершился успешно, и все добавленные записи были записаны в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 E_FAIL  
 Произошла ошибка, зависящая от поставщика. Получите сведения об ошибке для конкретного текста ошибки из поставщика.  
  
 E_UNEXPECTED  
 Метод был вызван для набора строк массового копирования, ранее не делает недействительными **IRowsetFastLoad::Commit** метод.  
  
## <a name="remarks"></a>Примечания  
 Объект [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] набору строк массового копирования поставщика OLE DB для собственного клиента ведет себя как набор строк в режиме отложенного обновления. Как пользователь вставляет данные строк через набор строк, добавленные строки обрабатываются так же, как ожидающие выполнения вставки на наборе строк, поддерживающем **IRowsetUpdate**.  
  
 Потребитель должен вызвать метод **зафиксировать** метод набору строк массового копирования, чтобы записать добавленные строки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы в так же, как **IRowsetUpdate::Update** метод используется для отправки ожидающих строк в экземпляр SQL Server.  
  
 Если потребитель освобождает ссылку на набор данных массового копирования без вызова **зафиксировать** метод, все добавленные строки не были записаны, теряются.  
  
 Потребитель может сгруппировать добавленные строки, вызвав **зафиксировать** метод с *fDone* аргумента значение FALSE. Когда *fDone*имеет значение TRUE, набор строк становится недействительным. Набор строк недопустимый массового копирования поддерживает только **ISupportErrorInfo** интерфейс и **IRowsetFastLoad::Release** метод.  
  
## <a name="see-also"></a>См. также  
 [IRowsetFastLoad &#40;OLE DB&#41;](irowsetfastload-ole-db.md)  
  
  
