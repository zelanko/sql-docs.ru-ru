---
title: Соединение с Oracle | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- connOra
ms.assetid: 711ac7ff-5d3d-4533-80ca-d1fecdb3048f
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 6d605a5ed646df46e90440780a08e32ae82ad390
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68099771"
---
# <a name="connect-to-oracle"></a>Соединение с Oracle

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  При первом добавлении или изменении таблиц, используемых на экземпляре CDC, программа может попросить установить соединение с базой данных Oracle. Необходимо ввести учетные данные пользователя Oracle, который имеет доступ к схеме отслеживаемых таблиц. Введите в этом диалоговом окне следующие данные:  
  
 **Проверка подлинности**  
  
 Выберите один из следующих вариантов:  
  
-   **Проверка подлинности Windows**. Выберите этот параметр, чтобы использовать учетные данные текущего пользователя Windows. Этот параметр можно использовать только в том случае, если в базе данных Oracle настроено использование проверки подлинности Windows.  
  
-   **Проверка подлинности Oracle**. Если выбран этот вариант, то нужно будет ввести **Имя пользователя** и **Пароль пользователя** в базе данных Oracle, с которой устанавливается соединение.  
  
## <a name="see-also"></a>См. также:  
 [Добавление таблиц в экземпляр CDC](../../integration-services/change-data-capture/add-tables-to-a-cdc-instance.md)  
  
  
