---
title: srv_message_handler (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: extended-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- srv_message_handler
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_message_handler
ms.assetid: 41bcd057-436f-4fa8-8293-fc8057a30877
caps.latest.revision: 31
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8eb5cff9bf0d4a79c0bbce3fcd35a981e0eda5e6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="srvmessagehandler-extended-stored-procedure-api"></a>srv_message_handler (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Вызывает установленный обработчик сообщений API-интерфейса расширенных хранимых процедур. Эта функция обычно используется для вызова [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из расширенной хранимой процедуры для регистрации ошибки (определенной расширенной хранимой процедурой) в файле журнала ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или журнале приложений [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int srv_message_handler (  
SRV_PROC *  
srvproc  
,  
int  
errornum  
,  
BYTE   
severity  
,  
BYTE  
state  
,  
int  
oserrnum  
,  
char *  
errtext  
,  
int  
errtextlen  
,  
char *  
oserrtext  
,  
int  
oserrtextlen  
);  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, который представляет собой дескриптор соединения с клиентом. Параметр *srvproc* содержит сведения, которые используются для управления связью и передачей данных между приложением и клиентом.  
  
 *errornum*  
 Номер ошибки, определенный расширенной хранимой процедурой. Это значение должно быть от 50 001 до 2 147 483 647.  
  
 *severity*  
 Стандартное значение серьезности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для ошибки. Это значение должно быть от 0 до 24.  
  
 *state*  
 Значение состояния [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для ошибки.  
  
 *oserrnum*  
 Номер ошибки операционной системы. Этот аргумент не учитывается.  
  
 *errtext*  
 Описание ошибки *errornum* расширенной хранимой процедуры.  
  
 *errtextlen*  
 Длина строки ошибки *errtext* расширенной хранимой процедуры.  
  
 *oserrtext*  
 Описание ошибки операционной системы *oserrnum*. Этот аргумент не учитывается.  
  
 *oserrtextlen*  
 Длина строки ошибки операционной системы *oserrtext*.  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Замечания  
 Функция **srv_message_handler** обеспечивает интеграцию расширенной хранимой процедуры с централизованными функциями регистрации ошибок и подготовки отчетов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Можно назначить предупреждения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для событий из расширенных хранимых процедур, и агент SQL Server будет отслеживать состояние этих предупреждений.  
  
 Если сообщение об ошибке длиннее, оно усекается до 412 байт.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
