---
title: Проверка сведений о секции (слияние)
description: Описание проверки сведений о секции для подписчика на публикацию слиянием в SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication data validation [SQL Server replication], partitions
- parameterized filters [SQL Server replication], validating partition information
- validating partition information
ms.assetid: c059553e-df2c-4333-ba79-e8d6e2890c34
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: da57b7586fb80346dda466004a9cd47a3bb08884
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "75321555"
---
# <a name="validate-partition-information-for-a-merge-subscriber"></a>Проверка сведений о секции для подписчика на публикацию слиянием
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  При определении параметризованного фильтра строк для публикации слиянием используется функция, ссылающаяся на данные подписчика, например на имя входа подписчика. По умолчанию репликация проверяет данные подписчика на основании этой функции перед каждой синхронизацией и при использовании моментального снимка на подписчике. Процесс проверки обеспечивает правильность секционирования данных для каждого подписчика. Характер проверки контролируется свойством публикации **validate_subscriber_info**, изменить которое можно при помощи процедуры [sp_changemergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md) или на странице **Параметры подписки** диалогового окна **Свойства публикаций**. Дополнительные сведения об изменении свойств публикаций см. в разделе [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
## <a name="how-partition-validation-works"></a>Сведения о работе проверки секции  
 Например, при фильтрации публикации при помощи функции **SUSER_SNAME()** агент слияния использует исходный моментальный снимок для каждого подписчика на основании данных, допустимых для выражения **SUSER_SNAME()** .  
  
 Если проверка включена, когда подписчик вновь подключается к издателю для следующей синхронизации, агент слияния проверяет данные на подписчике и гарантирует, что каждая секция подписчика является именно той секцией, которая была получена в исходном моментальном снимке. Для каждого последующего применения слияния или моментального снимка агент слияния проверяет каждую секцию подписчика.  
  
 Если агент слияния обнаруживает, что функция, используемая в выражении фильтрации, возвращает значение, отличное от значения, бывшего при исходном моментальном снимке, слияние или применение моментального снимка завершается ошибкой, и для этой подписки подписчика может понадобиться повторная инициализация. Повторная инициализация может быть необходимой для предотвращения проблем в случае изменения установки слияния подписчика, но может быть достаточно изменить информацию на подписчике, например имя входа, и вернуть ее к значению, которое использовалось во время исходного моментального снимка.  
  
 Когда агент слияния проверяет секцию, наряду с проверкой значений секции, возвращаемых функциями, используемыми в выражениях фильтрации, агент проверяет также, сформирован ли моментальный снимок перед изменениями, которые сделали его недействительным, например перед выполнением операций очистки метаданных или изменениями схемы. Если секционированный моментальный снимок слишком стар, агент слияния возвращает ошибку, и пользователь должен вновь сформировать секционированный моментальный снимок для этого подписчика на основании текущего стандартного моментального снимка.  
  
## <a name="see-also"></a>См. также:  
 [Вопросы и ответы об администрировании репликации](../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md)   
 [Best Practices for Replication Administration](../../relational-databases/replication/administration/best-practices-for-replication-administration.md)   
 [Повторная инициализация подписок](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Проверка реплицированных данных](../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  
