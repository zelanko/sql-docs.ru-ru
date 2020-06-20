---
title: Справочник по программированию расширенных хранимых процедур | Документы Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- extended stored procedures [SQL Server], listed
ms.assetid: 4e9d0374-0927-4f17-bab9-2215b1b8fea8
author: rothja
ms.author: jroth
ms.openlocfilehash: 23141b6d377333837e3416978d67424352075e75
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050821"
---
# <a name="extended-stored-procedures-programmer39s-reference"></a>Справочник программистов по расширенным хранимым процедурам&#39;
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)]API расширенных хранимых процедур, который ранее был частью службы Open Data Services, предоставляет серверный интерфейс прикладного программирования (API) для расширения [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] функциональных возможностей. API состоит из функций и макросов на языке C и C++, используемых для построения приложений.  
  
 С появлением новых и более мощных технологий, таких как интеграция со средой CLR, необходимость расширенных хранимых процедур значительно уменьшилась.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="in-this-section"></a>В этом разделе  
  
|||  
|-|-|  
|[Типы данных](srv-pfield-extended-stored-procedure-api.md)|  
|[srv_alloc](srv-alloc-extended-stored-procedure-api.md)||  
|[srv_convert](srv-pfieldex-extended-stored-procedure-api.md)|  
|[srv_describe](srv-rpcdb-extended-stored-procedure-api.md)|  
|[srv_getbindtoken](srv-rpcname-extended-stored-procedure-api.md)|  
|[srv_got_attention](srv-rpcnumber-extended-stored-procedure-api.md)|  
||[srv_rpcoptions](srv-rpcoptions-extended-stored-procedure-api.md)|  
|[srv_message_handler](srv-rpcowner-extended-stored-procedure-api.md)|  
|[srv_paramdata](srv-rpcparams-extended-stored-procedure-api.md)|  
|[srv_paraminfo](srv-senddone-extended-stored-procedure-api.md)|  
|[srv_paramlen](srv-sendmsg-extended-stored-procedure-api.md)|  
|[srv_parammaxlen](srv-sendrow-extended-stored-procedure-api.md)|  
|[srv_paramname](srv-setcoldata-extended-stored-procedure-api.md)|  
|[srv_paramnumber](srv-setcollen-extended-stored-procedure-api.md)|  
|[srv_paramset](srv-setutype-extended-stored-procedure-api.md)|  
|[srv_paramsetoutput](srv-willconvert-extended-stored-procedure-api.md)|  
|[srv_paramstatus](srv-wsendmsg-extended-stored-procedure-api.md)|  
|[srv_paramtype](srv-paramtype-extended-stored-procedure-api.md)||  
  
  
