---
title: Пароль распространителя | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.configuredistributionwizard.distributorpassword.f1
ms.assetid: 52787c5e-c9ef-440e-a000-0787111b7dbb
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: c9a5e8924139cf01a75bf48407c769a839a77f5e
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770655"
---
# <a name="distributor-password"></a>Пароль распространителя
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Если на странице **Издатели** данного мастера пользователь включил одного или нескольких издателей для использования данного сервера в качестве удаленного распространителя, то необходимо задать пароль для соединения, устанавливаемого репликацией, между издателем и удаленным распространителем, используя имя входа **distributor_admin** . Тот же пароль необходимо ввести для каждого издателя, использующего этот удаленный распространитель, на странице **Административный пароль** мастера создания публикаций или мастера настройки распространения. Дополнительные сведения о безопасности распространителей см. в разделе [Защита распространителя](../../relational-databases/replication/security/secure-the-distributor.md).  
  
## <a name="options"></a>Параметры  
 **Пароль**  
 Введите надежный пароль для соединения между издателем и удаленным распространителем.  
  
 **Подтвердите пароль**  
 Повторно введите пароль, чтобы подтвердить правильность ввода.  
  
## <a name="see-also"></a>См. также:  
 [Настройка распространения](../../relational-databases/replication/configure-distribution.md)   
 [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md)  
  
  
