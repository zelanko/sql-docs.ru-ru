---
title: srv_senddone (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 2bce064ee38082861e9b6c5d4f2c6e28bf41dded
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62745525"
---
# <a name="srvsenddone-extended-stored-procedure-api"></a>srv_senddone (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
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
  
## <a name="remarks"></a>Примечания  
 По запросу клиента сервер может выполнить ряд команд и вернуть несколько результирующих наборов. Для каждого результирующего набора функция **srv_senddone** должна вернуть клиенту сообщение о завершении с результатом.  
  
 Поле *count* указывает количество строк, затронутых командой. Если в поле *count* содержится значение счетчика, то в поле *status* должен быть установлен флаг SRV_DONE_COUNT. Это значение позволяет клиенту провести различие между значением *count* (равным 0) и неиспользуемым полем *count* .  
  
 Нельзя вызывать функцию **srv_senddone** из обработчика SRV_CONNECT.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
