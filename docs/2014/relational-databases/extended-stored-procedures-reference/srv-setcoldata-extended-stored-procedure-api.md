---
title: srv_setcoldata (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_setcoldata
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_setcoldata
ms.assetid: 2e19205a-25ca-4d4a-916b-d591cf2c892b
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: fd84bacfd389651abaf00486cd9940d95a26b0b3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62745575"
---
# <a name="srvsetcoldata-extended-stored-procedure-api"></a>srv_setcoldata (API-интерфейс расширенных хранимых процедур)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Указывает текущий адрес для данных столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int srv_setcoldata (  
SRV_PROC *  
srvproc  
,  
int   
column  
,  
void *  
data   
);  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, который представляет собой дескриптор соединения с клиентом. Эта структура содержит сведения, которые используются библиотекой API-интерфейса расширенных хранимых процедур для управления связью и передачи данных между приложением и клиентом.  
  
 *column*  
 Указывает номер столбца, для которого задается адрес. Нумерация столбцов начинается с 1.  
  
 *data*  
 Указатель для данных столбца. Память, выделенная для *data* , не должна освобождаться до замены данных столбца с помощью еще одного вызова метода **srv_setcoldata**или **srv_senddone** .  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Примечания  
 Каждый столбец строки должен быть сначала определен с помощью метода **srv_describe**. Адреса данных столбцов первоначально задаются с помощью метода **srv_describe**. При изменении адреса данных столбца необходимо вызвать метод **srv_setcoldata** , чтобы указать новый адрес данных. Метод **srv_setcoldata** необходимо вызывать для каждого измененного столбца в отдельности.  
  
 Данные, содержащие значения NULL, представляются путем задания длины столбца в 0 с помощью метода **srv_setcollen**. В этом случае адрес данных будет пропущен.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>См. также  
 [srv_describe (интерфейс API расширенных хранимых процедур)](srv-describe-extended-stored-procedure-api.md)  
  
  
