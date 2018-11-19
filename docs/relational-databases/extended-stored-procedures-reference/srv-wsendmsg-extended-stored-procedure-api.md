---
title: srv_wsendmsg (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_wsendmsg
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_wsendmsg
ms.assetid: f2153076-32c9-4a52-8e1b-fc9618153543
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c49d9e3ac3ba60ded98c7bdba55465b914bf1b28
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51671423"
---
# <a name="srvwsendmsg-extended-stored-procedure-api"></a>srv_wsendmsg (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Отправляет клиенту сообщение в Юникоде.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int srv_wsendmsg(SRV_PROC *   
srvproc  
, int   
msgnum  
, int   
severity  
, WCHAR *   
message  
, int   
msglen  
);  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, который представляет собой дескриптор соединения с клиентом. Эта структура содержит сведения, которые используются библиотекой API-интерфейса расширенных хранимых процедур для управления связью и передачи данных между приложением и клиентом.  
  
 *Msgnum*  
 4-байтовый номер сообщения.  
  
 *Severity*  
 Указывает серьезность ошибки. Серьезность, меньше или равная 10, считается информационным сообщением, в противном случае — ошибкой.  
  
 *message*  
 Является указателем на строку в Юникоде, которая должна быть отправлена клиенту.  
  
 *msglen*  
 Указывает длину *message*в символах.  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Remarks  
 Эта функция используется для отправки сообщения в Юникоде. Она сходна с функцией **srv_sendmsg**, но сообщение, которое она отправляет, является строкой типа WCHAR, а не строкой типа DBCHAR. Следует отметить, что длина сообщения считается в символах, а не в байтах, а также *msglen* никогда не будет равно SRV_NULLTERM.  
  
 Функция возвращает значение FAIL, если:  
  
-   значение *msglen* лежит вне диапазона 0-32242;  
  
-   значение *msglen* равно 0, но значение указателя сообщения равно NULL;  
  
-   при отправке сообщения об ошибке через сеть возникает ошибка.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409 https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>См. также:  
 [srv_sendmsg (интерфейс API расширенных хранимых процедур)](../../relational-databases/extended-stored-procedures-reference/srv-sendmsg-extended-stored-procedure-api.md)  
  
  
