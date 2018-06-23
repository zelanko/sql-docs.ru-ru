---
title: IRowsetFastLoad::Commit (OLE DB) | Документы Microsoft
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 553f3aaaceae23944ae9b2d0be7d8129a22c0dd1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101973"
---
# <a name="irowsetfastloadcommit-ole-db"></a>IRowsetFastLoad::Commit (OLE DB)
  Обозначает конец пакета вставляемых строк и записывает эти строки в таблицу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Примеры см. в разделе [массового копирования данных с помощью IRowsetFastLoad &#40;OLE DB&#41; ](irowsetfastload-ole-db.md) и [отправить данные больших двоичных ОБЪЕКТОВ SQL SERVER с помощью IROWSETFASTLOAD и ISEQUENTIALSTREAM &#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md).  
  
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
 Метод был вызван для набора строк массового копирования, ранее недействительными **IRowsetFastLoad::Commit** метод.  
  
## <a name="remarks"></a>Примечания  
 Объект [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] набору строк массового копирования поставщика OLE DB для собственного клиента ведет себя как набор строк в режиме отложенного обновления. При добавлении данных строк с помощью набора строк, добавленные строки обрабатываются так же, как ожидающие выполнения вставки на наборе строк, поддерживающем **IRowsetUpdate**.  
  
 Пользователь должен вызвать **зафиксировать** метод набору строк массового копирования, чтобы записать добавленные строки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицу так же, как **IRowsetUpdate::Update** метод используется для отправки ожидающих строк экземпляр SQL Server.  
  
 Если потребитель освобождает ссылку на набор данных массового копирования без вызова **зафиксировать** метод, все добавленные строки не были записаны, теряются.  
  
 Пользователь может сгруппировать добавленные строки, вызвав **зафиксировать** метод с *fDone* аргумента значение FALSE. Когда *fDone*имеет значение TRUE, набор строк становится недействительным. Строк недопустимый массового копирования поддерживаются только **ISupportErrorInfo** интерфейс и **IRowsetFastLoad::Release** метод.  
  
## <a name="see-also"></a>См. также  
 [IRowsetFastLoad &#40;OLE DB&#41;](irowsetfastload-ole-db.md)  
  
  