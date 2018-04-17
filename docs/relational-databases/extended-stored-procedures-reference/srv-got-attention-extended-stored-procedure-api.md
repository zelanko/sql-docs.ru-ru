---
title: srv_got_attention (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
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
- srv_got_attention
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_got_attention
ms.assetid: 805e68e1-d17f-41bd-8b9f-a27283bb6fbe
caps.latest.revision: 17
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 88919fa49417b574d8af06619f6d362aebf86e85
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="srvgotattention-extended-stored-procedure-api"></a>srv_got_attention (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Проверяет, следует ли прервать выполнение текущего задания или разорвать соединение, и возвращает TRUE, если текущее задание было прервано или соединение разорвано.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL srv_got_attention (SRV_PROC *   
srvproc  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 *srvproc*  
 Указатель, определяющий подключение к базе данных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает TRUE, если выполнение текущего пакета было прервано или соединение разорвано. Возвращает FALSE, если текущий пакет по-прежнему выполняется или соединение существует.  
  
## <a name="remarks"></a>Замечания  
 Расширенная хранимая процедура, которая выполняется в течение длительного времени, должна периодически проверять соединение с сервером путем вызова функции **srv_got_attention**, чтобы завершиться, когда прерывается выполнение текущего пакета или разрывается соединение.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
