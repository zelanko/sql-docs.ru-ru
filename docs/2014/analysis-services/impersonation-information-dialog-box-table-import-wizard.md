---
title: Диалоговое окно сведений о олицетворения (мастер импорта таблиц) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.impersonationinfo.f1
ms.assetid: bee7eee5-0650-41f1-a372-5076ae97a58c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6592d81e91e0582c79bc1a8bb1264b6ab9a7b733
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66080698"
---
# <a name="impersonation-information-dialog-box-table-import-wizard"></a>Диалоговое окно «Сведения об олицетворении» (мастер импорта таблиц)
  Страница **Сведения об олицетворении** служит для указания учетных данных, которые будут использоваться [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] для соединения с источником данных. Дополнительные сведения об олицетворении учетных данных см. в разделе [Impersonation &#40;SSAS Tabular&#41;](tabular-models/impersonation-ssas-tabular.md).  
  
## <a name="options"></a>Параметры  
 **Конкретное имя пользователя Windows и пароль**  
 Выберите этот параметр, чтобы в табличной модели использовались учетные данные безопасности указанной пользовательской учетной записи Windows.  
  
 **Имя пользователя**  
 Введите требуемые домен и имя пользовательской учетной записи. Используйте следующий формат:  
  
 *\<Имя домена >* **\\**  *\<учетную запись пользователя >*  
  
 Этот параметр будет включен только в случае выбора параметра **Использовать указанные имя пользователя и пароль** .  
  
 **Пароль**  
 Введите пароль учетной записи пользователя, которая будет использоваться табличной моделью.  
  
 Этот параметр будет включен только в случае выбора параметра **Использовать указанные имя пользователя и пароль** .  
  
 **Учетная запись службы**  
 Выберите этот параметр для использования учетных данных безопасности, связанных со службой [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , управляющей моделью.  
  
## <a name="see-also"></a>См. также  
 [Олицетворение (табличные службы SSAS)](tabular-models/impersonation-ssas-tabular.md)  
  
  
