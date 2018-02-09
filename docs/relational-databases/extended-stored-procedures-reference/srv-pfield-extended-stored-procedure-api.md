---
title: "srv_pfield (интерфейс API расширенных хранимых процедур) | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
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
- srv_pfield
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_pfield
ms.assetid: a61e4c1f-e65b-48ea-a7d1-3e1544af389d
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 157bf19237d3b2dcf64a1401823c746fd2849cf0
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="srvpfield-extended-stored-procedure-api"></a>srv_pfield (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Пользуйтесь вместо этого интеграцией со средой CLR.  
  
 Возвращает сведения о подключении к базе данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DBCHAR * srv_pfield (  
SRV_PROC *  
srvproc  
,  
int   
field  
,  
int *  
len  
);  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель, определяющий подключение к базе данных.  
  
 *field*  
 Задает возвращаемые сведения о соединении.  
  
|Значение|Возвращает|  
|-----------|-------------|  
|SRV_APPLNAME|Имя приложения, задаваемое клиентом при установлении соединения.|  
|SRV_BCPFLAG|Флаг, имеющий значение TRUE, если клиент готовится к операции массового копирования, и FALSE в противном случае.|  
|SRV_CLIB|Имя библиотеки, позволяющей клиенту общаться с сервером.|  
|SRV_CPID|Идентификатор клиентского процесса на клиентском компьютере-источнике.|  
|SRV_HOST|Имя клиентского компьютера, сообщаемое клиентом при установлении соединения.|  
|SRV_LIBVERS|Версия клиентской библиотеки.|  
|SRV_LSECURE|Флаг. Имеет значение TRUE, если соединение использует для входа в систему встроенную безопасность Windows.|  
|SRV_NETWORK_MODULE|Имя сетевой библиотеки DLL, используемой соединением.|  
|SRV_NETWORK_VERSION|Версия сетевой библиотеки DLL, используемой соединением.|  
|SRV_NETWORK_CONNECTION|Строка соединения, передаваемая в сетевую библиотеку DLL и используемая для текущего соединения *srvproc*.|  
|SRV_PIPEHANDLE|Строка, содержащая дескриптор канала подключенного клиента, или NULL, если клиент подключен по сети, не использующей именованные каналы. Для использования этого дескриптора как допустимого дескриптора канала в [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows строку нужно преобразовать в числовой формат.|  
|SRV_RMTSERVER|Сервер, с которого вошел в систему клиентский процесс. Если вход в систему выполнялся с клиента, значение представляет собой пустую строку.|  
|SRV_ROWSENT|Количество строк, уже переданных процессом *srvproc* для текущего набора результатов.|  
|SRV_SPID|Идентификатор серверного потока *srvproc*. Для расширенных хранимых процедур это значение совпадает со столбцом **kpid**  таблицы **sys.sysprocesses** и может изменяться со временем.|  
|SRV_SPROC_CODEPAGE|Кодовая страница, используемая сервером для интерпретации данных в многобайтовой кодировке.|  
|SRV_STATUS|Текущее состояние *srvproc*: запущена или закрыта|  
|SRV_TYPE|Тип соединения *srvproc*. Если возвращается значение server, *srvproc* принадлежит экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если возвращается значение client, *srvproc* принадлежит клиенту DB-Library или ODBC.|  
|SRV_USER|Имя пользователя, которое использовалось для установки соединения.|  
|||  
  
 *len*  
 Представляет собой указатель на переменную **int**, в которой хранится длина возвращаемого значения *field*. Если значение *len* равно NULL, длина строки не возвращается.  
  
## <a name="returns"></a>Возвращает  
 Указатель на оканчивающуюся нулевым байтом строку, содержащую текущее значение указанного поля в процедуре SRV_PROC. Если поле пусто, то возвращается допустимый указатель на пустую строку, а *len* содержит 0. Если поле неизвестно, то возвращается значение NULL, а *len* содержит значение –1.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Дополнительные сведения об исследовании и проверке безопасности см. в [Центре разработчиков безопасности](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
