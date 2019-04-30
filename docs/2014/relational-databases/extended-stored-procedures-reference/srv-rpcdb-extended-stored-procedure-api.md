---
title: srv_rpcdb (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcdb
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcdb
ms.assetid: d52bfd22-7a7c-4ab0-af65-df96ff359e6f
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7eb462881ab9ae5d6221498a84fc2b79e0524bc9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63046659"
---
# <a name="srvrpcdb-extended-stored-procedure-api"></a>srv_rpcdb (API-интерфейс расширенных хранимых процедур)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Возвращает компонент имени базы данных для текущей удаленной хранимой процедуры.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DBCHAR * srv_rpcdb (  
SRV_PROC * srvproc,int *len );  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, который представляет собой дескриптор соединения с клиентом. Эта структура содержит сведения, которые используются библиотекой API-интерфейса расширенных хранимых процедур для управления связью и передачи данных между приложением и клиентом.  
  
 *len*  
 Указатель на переменную типа `int`, которая получает длину имени базы данных. Если переменная *len* имеет значение NULL, длина имени базы данных не возвращается.  
  
## <a name="returns"></a>Возвращает  
 Указатель DBCHAR на строку, оканчивающуюся нулевым байтом, для части текущей удаленной хранимой процедуры, представляющей имя базы данных. При отсутствии текущей удаленной хранимой процедуры возвращается значение NULL, а параметру *len* присваивается значение –1.  
  
## <a name="remarks"></a>Примечания  
 Эта функция возвращает только компонент базы данных из имени объекта удаленной хранимой процедуры. Он не включает ни необязательные описатели для владельца, ни имя и номер удаленной хранимой процедуры.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409 https://msdn.microsoft.com/security/).  
  
  
