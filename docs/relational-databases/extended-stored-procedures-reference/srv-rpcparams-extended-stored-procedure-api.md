---
title: srv_rpcparams (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
description: Сведения о srv_rpcparams и о том, как она может возвращать количество параметров для текущей удаленной хранимой процедуры.
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_rpcparams
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcparams
ms.assetid: 96a5e6f6-d320-4623-b96e-0a856e3abebb
author: rothja
ms.author: jroth
ms.openlocfilehash: 47fa4b7a539f1491d539b73fdcc50a9b298db910
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87248263"
---
# <a name="srv_rpcparams-extended-stored-procedure-api"></a>srv_rpcparams (API-интерфейс расширенных хранимых процедур)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Возвращает количество параметров для текущей удаленной хранимой процедуры.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int srv_rpcparams ( SRV_PROC *  
srvproc   
);  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, представляющую собой дескриптор соединения с клиентом (в данном случае — дескриптор, получивший удаленную хранимую процедуру). Структура содержит сведения, которые используются библиотекой API-интерфейса расширенных хранимых процедур для управления связью и передачи данных между приложением и клиентом.  
  
## <a name="returns"></a>Результаты  
 Количество параметров удаленной хранимой процедуры. Если удаленная хранимая процедура не имеет параметров или отсутствует текущая удаленная хранимая процедура, то возвращается значение -1 и возникает информационная ошибка.  
  
## <a name="remarks"></a>Remarks  
 Эта функция возвращает количество параметров текущей удаленной хранимой процедуры. Обычно она вызывается из удаленной хранимой процедуры.  
  
 Когда удаленная хранимая процедура вызывается с параметрами, эти параметры могут быть переданы либо по имени, либо по позиции — без указания имени. Если при вызове удаленной хранимой процедуры часть параметров была передана по имени, а часть — по позиции, то возникнет ошибка. В этом случае будет вызван обработчик удаленной хранимой процедуры, однако он не получает параметры, и **srv_rpcparams** вернет значение 0.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
