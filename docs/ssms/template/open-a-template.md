---
title: Открытие шаблона | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-templates
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- templates [Transact-SQL], opening
- opening templates
ms.assetid: 605b0f4c-5ba1-4249-ad1c-6341df77cd7a
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ce474af9d4c5753dd6b4c064338ca7cdb22db5cd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="open-a-template"></a>Открытие шаблона
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Можно открыть шаблон в обозревателе шаблонов.  
  
## <a name="to-open-a-template-from-template-explorer"></a>Открытие шаблона в Обозревателе шаблонов  
Можно открыть шаблоны в обозревателе шаблонов.  
  
1.  Чтобы открыть обозреватель шаблонов, выберите пункт **Обозреватель шаблонов** в меню **Вид**.  
  
2.  В списке категорий шаблонов разверните категорию, в которой находится нужный шаблон.  
  
3.  Предусмотрены три способа открыть шаблон.  
  
    1.  Дважды щелкните шаблон, чтобы открыть его в окне редактора кода.  
  
    2.  Щелкните шаблон правой кнопкой мыши и выберите в меню пункт **Открыть** , чтобы открыть его в окне редактора кода.  
  
    3.  Перетащите шаблон в окно редактора кода, чтобы добавить код шаблона в содержимое окна редактора.  
  
Нужные значения аргументов открытого шаблона задаются в окне **Замена параметров шаблона** .  
  
При открытии шаблона запускается новое окно редактора. Окно редактора откроется с учетными данными текущего активного соединения. Например, если выбрать экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde_md.md)] в обозревателе объектов при открытии шаблона CREATE DATABASE, откроется новое окно редактора кода с подключением к этому экземпляру. Если активных соединений нет, [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)] представит диалоговое окно входа.  
  
## <a name="see-also"></a>См. также:  
[Вид](../../ssms/template/template-explorer.md)  
[Замена параметров шаблона](../../ssms/template/replace-template-parameters.md)  
  
