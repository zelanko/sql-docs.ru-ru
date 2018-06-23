---
title: Метод IBCPSession::BCPReadFmt (OLE DB) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IBCPSession::BCPReadFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPReadFmt method
ms.assetid: e2a12050-94e4-48a3-8a48-b780d646f116
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f47369cb66f6695ca7a235beb72536ce34495bb5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195383"
---
# <a name="ibcpsessionbcpreadfmt-ole-db"></a>Метод IBCPSession::BCPReadFmt (OLE DB)
  Считывает сведения о формате для каждого столбца из файла форматирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT BCPReadFmt(   
const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>Примечания  
 Метод **BCPReadFmt** используется для считывания данных из файла форматирования, указывающего формат данных в файле данных. Данный метод способен определить правильную версию файла форматирования. Он может автоматически определить, в каком формате находится файл форматирования — XML или формат текста по старому стилю, —и действовать соответствующим образом. Поддерживаемые версии файла форматирования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] программа BCP поставщика OLE DB для собственного клиента имеют версию 6.0 или более поздней версии.  
  
 После **BCPReadFmt** метод считывает значения формата, он выполняет соответствующие вызовы [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) и [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) методы. Пользователю не требуется производить анализ файла форматирования и выполнять эти вызовы.  
  
 Чтобы сохранить файл форматирования, вызовите [IBCPSession::BCPWriteFmt](ibcpsession-bcpwritefmt-ole-db.md) метод. Вызовы метода **BCPReadFmt** могут ссылаться на сохраненные форматы. Кроме того, программа массового копирования (**bcp**) может сохранять определяемые пользователем форматы данных в файлах, на которые может ссылаться метод **BCPReadFmt** .  
  
 `BCP_OPTION_DELAYREADFMT` Значение *eOption* параметр [IBCPSession::BCPControl](ibcpsession-bcpcontrol-ole-db.md) изменяет поведение IBCPSession::BCPReadFmt.  
  
## <a name="arguments"></a>Аргументы  
 *pwszFormatFile*[in]  
 Путь и имя файла, содержащего значения формата для файла данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 S_OK  
 Метод выполнен успешно.  
  
 E_FAIL  
 Произошла ошибка поставщика, для использования подробных сведений [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) интерфейса.  
  
 E_OUTOFMEMORY  
 Ошибка, связанная с нехваткой памяти.  
  
 E_UNEXPECTED  
 Непредвиденный вызов метода. Например [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) перед вызовом этого метода не был вызван метод.  
  
## <a name="see-also"></a>См. также  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [Выполнение операций массового копирования](../native-client/features/performing-bulk-copy-operations.md)  
  
  