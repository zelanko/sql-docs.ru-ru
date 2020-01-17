---
title: Копирование состояния аспекта управления на основе политик в XML-файл
description: Сведения о копировании состояния аспекта управления на основе политик в XML-файл в с помощью SQL Server Management Studio (SSMS).
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, copy facet state to XML file
ms.assetid: 7d604ab1-6dd6-4f8e-a79c-eba99ab106fd
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: fa0ee70601b11af3341483aff177ef6a7a389ba6
ms.sourcegitcommit: 035ad9197cb9799852ed705432740ad52e0a256d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/31/2019
ms.locfileid: "75558205"
---
# <a name="copy-a-policy-based-management-facet-state-to-an-xml-file"></a>Копирование состояния аспекта управления на основе политик в XML-файл
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описывается копирование состояния аспекта управления на основе политик в XML-файл в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Копирование состояния аспекта в XML-файл с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Для процедуры в этом разделе требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-copy-a-facet-state-to-an-xml-file"></a>Копирование состояния аспекта в XML-файл  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], объект экземпляра, базу данных или объект базы данных и выберите команду **Аспекты**.  
  
2.  В диалоговом окне **Просмотр аспектов —** _имя_объекта_ щелкните **Экспортировать текущее состояние как политику**.  
  
3.  Введите имя и путь к файлу в диалоговом окне **Экспортировать как политику** либо найдите файл при помощи кнопки "Обзор" ( **...** ) и введите имя XML-файла. Дополнительные сведения о доступных параметрах данного диалогового окна см. в разделе [Export As Policy Dialog Box](../../relational-databases/policy-based-management/export-as-policy-dialog-box.md)  
  
4.  После завершения нажмите кнопку **ОК**.  
  
  
