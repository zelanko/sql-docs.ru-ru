---
title: "srv_senddone (интерфейс API расширенных хранимых процедур) | Документы Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- srv_senddone
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_senddone
ms.assetid: 1fc4f1d5-56d4-43f6-b5e4-0c0cc295cba3
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5f45177df0d252f3bd33475c20c60383f71f7ae7
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="srvsenddone-extended-stored-procedure-api"></a>srv_senddone (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Пользуйтесь вместо этого интеграцией со средой CLR.  
  
 Передает клиенту сообщение о результатах завершения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int srv_senddone (  
SRV_PROC *  
srvproc  
,  
DBUSMALLINT   
status  
,  
DBUSMALLINT  
info  
,  
DBINT  
count   
);  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, который представляет собой дескриптор соединения с клиентом (в данном случае — дескриптор, который получил запрос языка). Структура содержит сведения, которые используются библиотекой API-интерфейса расширенных хранимых процедур для управления связью и передачи данных между приложением и клиентом.  
  
 *status*  
 Представляет собой двухбайтовое поле для различных флагов *status* . С помощью логических операторов И и ИЛИ можно задавать сразу несколько флагов *status* . В следующей таблице перечислены возможные флаги *status* .  
  
|Флаг состояния|Описание|  
|-----------------|-----------------|  
|SRV_DONE_COUNT|Параметр *count* содержит допустимое значение счетчика.|  
|SRV_DONE_ERROR|Текущая клиентская команда получила ошибку.|  
  
 *info*  
 Зарезервированное поле длиной 2 байта. Присвойте этому параметру значение 0.  
  
 *count*  
 Поле размером 4 байта, используемое как счетчик текущего результирующего набора. Если в поле *status* установлен флаг SRV_DONE_COUNT, поле *count* содержит допустимое значение счетчика.  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL  
  
## <a name="remarks"></a>Remarks  
 По запросу клиента сервер может выполнить ряд команд и вернуть несколько результирующих наборов. Для каждого результирующего набора функция **srv_senddone** должна вернуть клиенту сообщение о завершении с результатом.  
  
 Поле *count* указывает количество строк, затронутых командой. Если в поле *count* содержится значение счетчика, то в поле *status* должен быть установлен флаг SRV_DONE_COUNT. Это значение позволяет клиенту провести различие между значением *count* (равным 0) и неиспользуемым полем *count* .  
  
 Нельзя вызывать функцию **srv_senddone** из обработчика SRV_CONNECT.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
