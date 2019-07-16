---
title: srv_sendmsg (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_sendmsg
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_sendmsg
ms.assetid: efcb50b9-f8ff-4121-bf67-05830171b928
author: rothja
ms.author: jroth
ms.openlocfilehash: 62fa2db01ff17008a0b6a7cd4e5fd0a2bce71189
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67910916"
---
# <a name="srvsendmsg-extended-stored-procedure-api"></a>srv_sendmsg (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Отправляет клиенту сообщение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int srv_sendmsg (  
SRV_PROC *  
srvproc  
,  
int  
msgtype  
,  
DBINT  
msgnum  
,  
DBTINYINT  
class  
,   
DBTINYINT  
state  
,  
DBCHAR *  
rpcname  
,  
int   
rpcnamelen  
,  
DBUSMALLINT  
linenum  
,  
DBCHAR *  
message  
,  
int  
msglen   
);  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, который представляет собой дескриптор соединения с клиентом (в данном случае — дескриптор, который получил запрос языка). Структура содержит сведения, которые используются библиотекой API-интерфейса расширенных хранимых процедур для управления связью и передачи данных между приложением и клиентом.  
  
 *msgtype*  
 Является либо SRV_MSG_INFO, либо SRV_MSG_ERROR, в зависимости от того, отправляет сервер информационное сообщение или сообщение об ошибке.  
  
 *msgnum*  
 4-байтовый номер сообщения.  
  
 *class*  
 Указывает серьезность ошибки. Серьезность, меньше или равная 10, считается информационным сообщением.  
  
 *state*  
 Предоставляет код состояния ошибки для текущего сообщения. Код состояния ошибки предоставляет информацию о контексте ошибки. Допустимые значения кода состояния — от 0 до 255.  
  
 *rpcname*  
 Не поддерживается в текущей версии.  
  
 *rpcnamelen*  
 Не поддерживается в текущей версии.  
  
 *linenum*  
 Представляет собой номер строки в пакете языковых команд, к которому относится сообщение. Номера строк начинаются с 1. Если параметр *linenum* не применяется к сообщению, установите его равным 0.  
  
 *message*  
 Является указателем на символьную строку, которая должна быть отправлена клиенту.  
  
 *msglen*  
 Задает длину *message* в байтах. Если *message*заканчивается нулевым байтом, задайте для параметра *msglen* значение SRV_NULLTERM.  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL  
  
## <a name="remarks"></a>Remarks  
 Эта функция отправляет клиенту сообщение об ошибке или информационное сообщение. Она вызывается один раз для каждой отправки сообщения.  
  
 Можно отправлять сообщения клиенту при помощи функции **srv_sendmsg** в любой последовательности перед тем или после того, как были отправлены все строки (если таковые были) при помощи функции **srv_sendrow**. Все сообщения, если таковые имеются, должны быть отправлены клиенту перед тем, как функция **srv_senddone** отправит состояние завершения.  
  
 Для отправки сообщений в Юникоде лучше использовать функцию **srv_wsendmsg**, чем функцию **srv_sendmsg**.  
  
 Дополнительные сведения см. в статье [Данные в Юникоде и кодовые страницы сервера](../../relational-databases/extended-stored-procedures-programming/unicode-data-and-server-code-pages.md).  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
