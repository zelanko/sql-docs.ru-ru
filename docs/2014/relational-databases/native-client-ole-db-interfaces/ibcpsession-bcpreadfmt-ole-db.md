---
title: IBCPSession::BCPReadFmt (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPReadFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPReadFmt method
ms.assetid: e2a12050-94e4-48a3-8a48-b780d646f116
author: rothja
ms.author: jroth
ms.openlocfilehash: be8d8ef1148cf77491099bc40224fe5cd4009af8
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85048004"
---
# <a name="ibcpsessionbcpreadfmt-ole-db"></a>Метод IBCPSession::BCPReadFmt (OLE DB)
  Считывает сведения о формате для каждого столбца из файла форматирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT BCPReadFmt(   
const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>Remarks  
 Метод **BCPReadFmt** используется для считывания данных из файла форматирования, указывающего формат данных в файле данных. Данный метод способен определить правильную версию файла форматирования. Он может автоматически определить, в каком формате находится файл форматирования — XML или формат текста по старому стилю, —и действовать соответствующим образом. Программа BCP поставщика OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает версии файла форматирования 6.0 и следующие.  
  
 После того как метод **BCPReadFmt** считывает значения формата, он выполняет соответствующие вызовы методов [IBCPSession::BCPColumns](ibcpsession-bcpcolumns-ole-db.md) и [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md). Пользователю не требуется производить анализ файла форматирования и выполнять эти вызовы.  
  
 Чтобы сохранить файл форматирования, вызовите метод [IBCPSession::BCPWriteFmt](ibcpsession-bcpwritefmt-ole-db.md). Вызовы метода **BCPReadFmt** могут ссылаться на сохраненные форматы. Кроме того, программа массового копирования (**bcp**) может сохранять определяемые пользователем форматы данных в файлах, на которые может ссылаться метод **BCPReadFmt** .  
  
 `BCP_OPTION_DELAYREADFMT`Значение параметра *eOption* [IBCPSession:: BCPControl](ibcpsession-bcpcontrol-ole-db.md) изменяет поведение IBCPSession:: BCPReadFmt.  
  
## <a name="arguments"></a>Аргументы  
 *pwszFormatFile*[in]  
 Путь и имя файла, содержащего значения формата для файла данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 S_OK  
 Метод выполнен успешно.  
  
 E_FAIL  
 Произошла ошибка, связанная с поставщиком. Подробные сведения можно получить с помощью интерфейса [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md).  
  
 E_OUTOFMEMORY  
 Ошибка, связанная с нехваткой памяти.  
  
 E_UNEXPECTED  
 Непредвиденный вызов метода. Например, перед вызовом этого метода не был вызван метод [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md).  
  
## <a name="see-also"></a>См. также:  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [Выполнение операций массового копирования](../native-client/features/performing-bulk-copy-operations.md)  
  
  
