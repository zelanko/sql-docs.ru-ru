---
title: Пароль распространителя | Документация Майкрософт
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rep.configuredistributionwizard.distributorpassword.f1
ms.assetid: 52787c5e-c9ef-440e-a000-0787111b7dbb
caps.latest.revision: 23
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 1278c8343510b790a7490c5799e574676d892fd8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36187970"
---
# <a name="distributor-password"></a>Пароль распространителя
  Если на странице **Издатели** данного мастера пользователь включил одного или нескольких издателей для использования данного сервера в качестве удаленного распространителя, то необходимо задать пароль для соединения, устанавливаемого репликацией, между издателем и удаленным распространителем, используя имя входа **distributor_admin** . Тот же пароль необходимо ввести для каждого издателя, использующего этот удаленный распространитель, на странице **Административный пароль** мастера создания публикаций или мастера настройки распространения. Дополнительные сведения о безопасности распространителей см. в разделе [Защита распространителя](security/secure-the-distributor.md).  
  
## <a name="options"></a>Параметры  
 **Пароль**  
 Введите надежный пароль для соединения между издателем и удаленным распространителем.  
  
 **Подтвердите пароль**  
 Повторно введите пароль, чтобы подтвердить правильность ввода.  
  
## <a name="see-also"></a>См. также  
 [Настройка распространения](configure-distribution.md)   
 [Настройка публикации и распространения](configure-publishing-and-distribution.md)  
  
  