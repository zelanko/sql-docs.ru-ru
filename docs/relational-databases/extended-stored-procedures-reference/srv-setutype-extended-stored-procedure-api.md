---
title: srv_setutype (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_setutype
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_setutype
ms.assetid: 6160f15d-1b68-411e-ab6d-491ec288f264
author: rothja
ms.author: jroth
ms.openlocfilehash: fedb0808c6071ec6a6ba9bb7bd985a43890cce3d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "75245072"
---
# <a name="srv_setutype-extended-stored-procedure-api"></a>srv_setutype (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Вместо этого используйте интеграцию со средой CLR.  
  
 Устанавливает определяемый пользователем тип данных для столбца строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int srv_setutype (  
SRV_PROC *  
srvproc  
,  
int   
column  
,   
DBINT  
user_type   
);  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, который представляет собой дескриптор соединения с клиентом. Эта структура содержит сведения, которые используются библиотекой API-интерфейса расширенных хранимых процедур для управления связью и передачи данных между приложением и клиентом.  
  
 *рубрик*  
 Указывает, какой столбец устанавливать. Нумерация столбцов начинается с 1.  
  
 *user_type*  
 Указывает код определяемого пользователем типа данных.  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL. Если столбец не существует, возвращает значение FAIL.  
  
## <a name="remarks"></a>Remarks  
 Столбец имеет два типа данных: фактический и определяемый пользователем. Определяемый пользователем тип данных используется [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для хранения фактического определяемого пользователем типа данных столбца, если таковые имеются, и сведения о описании столбца, такие как допустимость значений NULL и возможность обновления для столбца.  
  
 Функцию **srv_setutype** можно вызвать в любое время после определения *column* с помощью функции **srv_describe** и до передачи последней строки.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](https://www.microsoft.com/msrc?rtc=1).  
  
## <a name="see-also"></a>См. также:  
 [API srv_describe &#40;расширенных хранимых процедур&#41;](../../relational-databases/extended-stored-procedures-reference/srv-describe-extended-stored-procedure-api.md)  
  
  
