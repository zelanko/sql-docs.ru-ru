---
title: Сведения об олицетворении-диалоговое окно (мастер импорта таблиц) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.bidtoolset.impersonationinfo.f1
ms.assetid: bee7eee5-0650-41f1-a372-5076ae97a58c
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c53b71a06904bd3f898efa3dd2d9946670193845
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188126"
---
# <a name="impersonation-information-dialog-box-table-import-wizard"></a>Диалоговое окно «Сведения об олицетворении» (мастер импорта таблиц)
  Страница **Сведения об олицетворении** служит для указания учетных данных, которые будут использоваться [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] для соединения с источником данных. Дополнительные сведения об олицетворении учетных данных см. в разделе [Impersonation &#40;SSAS Tabular&#41;](tabular-models/impersonation-ssas-tabular.md).  
  
## <a name="options"></a>Параметры  
 **Указанные имя пользователя и пароль**  
 Выберите этот параметр, чтобы в табличной модели использовались учетные данные безопасности указанной пользовательской учетной записи Windows.  
  
 **Имя пользователя**  
 Введите требуемые домен и имя пользовательской учетной записи. Используйте следующий формат:  
  
 *\<Имя домена >* **\\**  *\<имя учетной записи пользователя >*  
  
 Этот параметр будет включен только в случае выбора параметра **Использовать указанные имя пользователя и пароль** .  
  
 **Пароль**  
 Введите пароль учетной записи пользователя, которая будет использоваться табличной моделью.  
  
 Этот параметр будет включен только в случае выбора параметра **Использовать указанные имя пользователя и пароль** .  
  
 **Учетная запись службы**  
 Выберите этот параметр для использования учетных данных безопасности, связанных со службой [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , управляющей моделью.  
  
## <a name="see-also"></a>См. также  
 [Олицетворение &#40;табличные службы SSAS&#41;](tabular-models/impersonation-ssas-tabular.md)  
  
  