---
title: srv_paramsetoutput (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
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
- srv_paramsetoutput
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_paramsetoutput
ms.assetid: f2810e19-e513-458b-8925-5756b6ee1313
caps.latest.revision: 29
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0297be0851d2d57afce891997b387932b16dbb0c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="srvparamsetoutput-extended-stored-procedure-api"></a>srv_paramsetoutput (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Устанавливает значение возвращаемого параметра. Эта функция заменяет функцию **srv_paramset**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int srv_paramsetoutput (  
SRV_PROC *  
srvproc  
,  
int  
n  
,  
BYTE *  
pbData  
,  
ULONG   
cbLen  
,  
BOOL  
fNull   
);  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Является дескриптором клиентского соединения.  
  
 *n*  
 Является порядковым номером параметра, который должен быть установлен. Первый параметр имеет значение 1.  
  
 *pbData*  
 Является указателем на значение данных, которое должно быть отправлено обратно клиенту как возвращаемый параметр процедуры.  
  
 *cbLen*  
 Является фактической длиной данных, которые должны быть возвращены. Если тип данных параметра указывает значения постоянной длины и не допускает значений NULL (например, *srvbit* или *srvint1*), аргумент*cbLen* не учитывается. Значение, равное 0, указывает на данные нулевой длины, если значение *fNull* равно FALSE.  
  
 *fNull*  
 Является флагом, показывающим, равно ли NULL значение возвращаемого параметра. Установите этот флаг в значение TRUE, если параметр должен быть установлен в значение NULL. Значение по умолчанию — FALSE. Если *fNull* установлен в значение TRUE, то аргумент *cbLen* должен быть установлен в значение 0, иначе функция завершится с ошибкой.  
  
## <a name="returns"></a>Возвращает  
 Если сведения о параметре были успешно установлены, возвращается значение SUCCEED, в противном случае — FAIL. Значение FAIL возвращается, если:  
  
-   параметр не является возвращаемым параметром, или  
  
-   аргумент *cbLen* недопустим.  
  
## <a name="remarks"></a>Замечания  
 **Примечание по безопасности.** Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные DLL-библиотеки перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
