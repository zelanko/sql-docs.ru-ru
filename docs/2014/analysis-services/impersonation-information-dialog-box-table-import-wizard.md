---
title: Диалоговое окно сведений о олицетворения (мастер импорта таблиц) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.impersonationinfo.f1
ms.assetid: bee7eee5-0650-41f1-a372-5076ae97a58c
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a5c9d9b49d41d8f9320ff414925bb4532145d16f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37245685"
---
# <a name="impersonation-information-dialog-box-table-import-wizard"></a>Диалоговое окно «Сведения об олицетворении» (мастер импорта таблиц)
  Страница **Сведения об олицетворении** служит для указания учетных данных, которые будут использоваться [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] для соединения с источником данных. Дополнительные сведения об олицетворении учетных данных см. в разделе [Impersonation &#40;SSAS Tabular&#41;](tabular-models/impersonation-ssas-tabular.md).  
  
## <a name="options"></a>Параметры  
 **Конкретное имя пользователя Windows и пароль**  
 Выберите этот параметр, чтобы в табличной модели использовались учетные данные безопасности указанной пользовательской учетной записи Windows.  
  
 **Имя пользователя**  
 Введите требуемые домен и имя пользовательской учетной записи. Используйте следующий формат:  
  
 *\<Имя домена >* ** \\ ** * \<учетную запись пользователя >*  
  
 Этот параметр будет включен только в случае выбора параметра **Использовать указанные имя пользователя и пароль** .  
  
 **Пароль**  
 Введите пароль учетной записи пользователя, которая будет использоваться табличной моделью.  
  
 Этот параметр будет включен только в случае выбора параметра **Использовать указанные имя пользователя и пароль** .  
  
 **Учетная запись службы**  
 Выберите этот параметр для использования учетных данных безопасности, связанных со службой [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , управляющей моделью.  
  
## <a name="see-also"></a>См. также  
 [Олицетворение &#40;табличные службы SSAS&#41;](tabular-models/impersonation-ssas-tabular.md)  
  
  
