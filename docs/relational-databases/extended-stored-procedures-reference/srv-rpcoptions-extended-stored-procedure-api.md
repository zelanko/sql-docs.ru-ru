---
title: srv_rpcoptions (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: extended-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- srv_rpcoptions
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcoptions
ms.assetid: dbcce5d1-d5a1-4379-9597-04e43af5923d
caps.latest.revision: 30
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: dab1afd35dd8e3f0b8336e8d839b0747e47385c8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32935550"
---
# <a name="srvrpcoptions-extended-stored-procedure-api"></a>srv_rpcoptions (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Возвращает параметры времени выполнения для текущей удаленной хранимой процедуры.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DBUSMALLINT srv_rpcoptions ( SRV_PROC *  
srvproc   
);  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, представляющую собой дескриптор соединения с клиентом (в данном случае — дескриптор, получивший удаленную хранимую процедуру). Эта структура содержит сведения, которые используются библиотекой API-интерфейса расширенных хранимых процедур для управления связью и передачей данных между приложением и клиентом.  
  
## <a name="returns"></a>Возвращает  
 Битовая карта, которая содержит флаги времени выполнения, соединенные логической операцией ИЛИ для текущей удаленной хранимой процедуры. При отсутствии текущей удаленной хранимой процедуры возвращается значение 0 и формируется сообщение.  
  
## <a name="remarks"></a>Remarks  
 В следующей таблице описывается каждый флаг времени выполнения.  
  
|Флаг времени выполнения|Description|  
|--------------------|-----------------|  
|SRV_NOMETADATA|Клиент запросил результаты без метаданных. Этот флаг используется, только когда клиент связывается с экземпляром [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Приложение API-интерфейса расширенных хранимых процедур не может исключить метаданные.|  
|SRV_RECOMPILE|Клиент запросил повторную компиляцию удаленной хранимой процедуры перед ее выполнением. Этот флаг не может применяться к приложению API-интерфейса расширенных хранимых процедур.|  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
