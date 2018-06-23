---
title: Вычисление политики управления на основе политик в контексте этой политики | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: 0b3214bd-d0ab-45ab-9281-3d95507abe54
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a1828ceb08481a3d41b05cd6735e6b2741827e6f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194003"
---
# <a name="evaluate-a-policy-based-management-policy-from-that-policy"></a>Вычисление политики управления на основе политик по этой политике
  В этом разделе описано вычисление политики в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Для вычисления политики используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-evaluate-a-policy"></a>Вычисление политики  
  
1.  В **обозревателе объектов**щелкните знак «плюс», чтобы развернуть сервер, содержащий политику, которую нужно вычислить.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Управление** .  
  
3.  Щелкните знак «плюс», чтобы развернуть папку **Управление политиками**.  
  
4.  Щелкните знак «плюс», чтобы развернуть папку **Политики** .  
  
5.  Щелкните правой кнопкой мыши политику, которую необходимо вычислить, и выберите пункт **Вычислить**.  
  
6.  В диалоговом окне **Анализ результатов**  показаны результаты вычисления политики. Для целевых объектов, не соответствующих политике и имеющих свойства, которые можно перенастроить с помощью управления на основе политик, соответствие политике можно включить принудительно, нажав кнопку **Применить**. Дополнительные сведения о параметрах, доступных в диалоговом окне **Вычисление политик** , см. в разделах [Evaluate Policies Dialog Box, Policy Selection Page](evaluate-policies-dialog-box-policy-selection-page.md) и [Evaluate Policies Dialog Box, Evaluation Results Page](evaluate-policies-dialog-box-evaluation-results-page.md).  
  
7.  После завершения нажмите кнопку **Закрыть**.  
  
  