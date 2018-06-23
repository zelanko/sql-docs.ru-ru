---
title: Копирование состояния аспекта управления на основе политик в XML-файл | Документация Майкрософт
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
- Policy-Based Management, copy facet state to XML file
ms.assetid: 7d604ab1-6dd6-4f8e-a79c-eba99ab106fd
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2b06ef970649f83fc11b017e8df65ff9e8151337
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193354"
---
# <a name="copy-a-policy-based-management-facet-state-to-an-xml-file"></a>Копирование состояния аспекта управления на основе политик в XML-файл
  В этом разделе описывается копирование состояния аспекта управления на основе политик в XML-файл в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Копирование состояния аспекта в XML-файл с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Для процедуры в этом разделе требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-copy-a-facet-state-to-an-xml-file"></a>Копирование состояния аспекта в XML-файл  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], объект экземпляра, базу данных или объект базы данных и выберите команду **Аспекты**.  
  
2.  В диалоговом окне **Просмотр аспектов —***имя объекта* щелкните **Экспортировать текущее состояние как политику**.  
  
3.  Введите имя и путь к файлу в диалоговом окне **Экспортировать как политику** либо найдите файл при помощи кнопки "Обзор" (**...**) и введите имя XML-файла. Дополнительные сведения о доступных параметрах данного диалогового окна см. в разделе [Export As Policy Dialog Box](export-as-policy-dialog-box.md)  
  
4.  После завершения нажмите кнопку **ОК**.  
  
  