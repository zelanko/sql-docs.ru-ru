---
title: srv_rpcoptions (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcoptions
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcoptions
ms.assetid: dbcce5d1-d5a1-4379-9597-04e43af5923d
author: rothja
ms.author: jroth
ms.openlocfilehash: 861c27e94d3717a4dbeba1fe5f2633c2604ee7c4
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050612"
---
# <a name="srv_rpcoptions-extended-stored-procedure-api"></a>srv_rpcoptions (API-интерфейс расширенных хранимых процедур)
    
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
 Указатель на структуру SRV_PROC, представляющую собой дескриптор соединения с клиентом (в данном случае — дескриптор, получивший удаленную хранимую процедуру). Эта структура содержит сведения, которые используются библиотекой API-интерфейса расширенных хранимых процедур для управления связью и передачи данных между приложением и клиентом.  
  
## <a name="returns"></a>Возвращаемое значение  
 Битовая карта, которая содержит флаги времени выполнения, соединенные логической операцией ИЛИ для текущей удаленной хранимой процедуры. При отсутствии текущей удаленной хранимой процедуры возвращается значение 0 и формируется сообщение.  
  
## <a name="remarks"></a>Remarks  
 В следующей таблице описывается каждый флаг времени выполнения.  
  
|Флаг времени выполнения|Описание|  
|--------------------|-----------------|  
|SRV_NOMETADATA|Клиент запросил результаты без метаданных. Этот флаг используется только в том случае, если клиент взаимодействует с экземпляром [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Приложение API-интерфейса расширенных хранимых процедур не может исключить метаданные.|  
|SRV_RECOMPILE|Клиент запросил повторную компиляцию удаленной хранимой процедуры перед ее выполнением. Этот флаг не может применяться к приложению API-интерфейса расширенных хранимых процедур.|  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
