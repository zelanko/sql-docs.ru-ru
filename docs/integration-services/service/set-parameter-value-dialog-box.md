---
title: "Задайте значение параметра-диалоговое окно | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: service
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce9c2201-4e9a-4495-948f-b68deeaa7955
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d2e74c467cc0f94d15bdd4a42a300a842012ecd5
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="set-parameter-value-dialog-box"></a>Диалоговое окно «Задание значения параметра»
  Диалоговое окно **Задание значения параметра** используется для настройки параметров и свойств диспетчеров соединений для пакетов и проектов.  
  
 **Выбор действия**  
  
-   [Открыть диалоговое окно «Задание значения параметра»](#open_dialog)  
  
-   [Настройка параметров](#option)  
  
##  <a name="open_dialog"></a> Открыть диалоговое окно «Задание значения параметра»  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]установите соединение с сервером служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
     Устанавливается соединение с экземпляром компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , в котором размещена база данных SSISDB.  
  
2.  В обозревателе объектов разверните дерево для отображения узла **Каталоги служб Integration Services** .  
  
3.  Разверните узел **SSISDB** .  
  
4.  Щелкните правой кнопкой мыши пакет, выберите **Настроить**, а затем нажмите кнопку с многоточием на вкладке **Параметры** или **Диспетчеры соединений** .  
  
##  <a name="option"></a> Настройка параметров  
 **Параметр**  
 Выводит список имен параметра.  
  
 **Тип**  
 Перечисляет тип данных значения параметра.  
  
 **Description**  
 Показывает дополнительное описание параметра.  
  
 **Изменить значение**  
 Выберите этот параметр, чтобы изменить значение параметра.  
  
 **Использовать значение по умолчанию из пакета**  
 Выберите этот параметр, чтобы использовать значение параметра по умолчанию, сохраненное в пакете.  
  
 **Использовать переменную среды**  
 Выберите этот параметр для использования значения переменной, сохраненного в среде, на которую ссылается проект или пакет. Чтобы добавить ссылку среды к проекту или пакету, используйте диалоговое окно **Настройка** . Дополнительные сведения см. в статье [Configure Dialog Box](../../integration-services/service/configure-dialog-box.md).  
  
  

