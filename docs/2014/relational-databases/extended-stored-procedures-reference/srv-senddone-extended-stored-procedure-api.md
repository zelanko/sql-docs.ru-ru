---
title: srv_senddone (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- srv_senddone
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_senddone
ms.assetid: 1fc4f1d5-56d4-43f6-b5e4-0c0cc295cba3
caps.latest.revision: 30
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 10d5f559d37b713064761dd2715038431f99817c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37283170"
---
# <a name="srvsenddone-extended-stored-procedure-api"></a>srv_senddone (API-интерфейс расширенных хранимых процедур)
    
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
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
