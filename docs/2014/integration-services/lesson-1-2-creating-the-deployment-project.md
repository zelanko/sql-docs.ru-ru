---
title: Шаг 2. Создание проекта развертывания | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 59990fe2-7036-4e9c-8efc-6ece9e66eda7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9c61b2e6941e94dbb8c399380d5b1e43262158af
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85436071"
---
# <a name="step-2-creating-the-deployment-project"></a>Шаг 2. Создание проекта развертывания
  В службах [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]развертываемый модуль находится в проекте служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Перед развертыванием пакетов нужно создать новый проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] и добавить в него все пакеты и вспомогательные файлы, которые нужно развертывать вместе с пакетами.  
  
### <a name="to-create-the-integration-services-project"></a>Создание проекта служб Integration Services  
  
1.  Нажмите кнопку **Пуск**, наведите указатель на пункт **Все программы**, наведите указатель на пункт **Microsoft SQL Server**и выберите пункт **SQL Server Data Tools**.  
  
2.  В меню **Файл** наведите указатель на пункт **Создать**и выберите пункт **Проект** , чтобы создать проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
3.  В диалоговом окне **Создание проекта** на панели **Шаблоны** выберите пункт **Проект служб SSIS** .  
  
4.  В поле **Имя** измените заданное по умолчанию имя на **Учебник по развертыванию**. При необходимости снимите флажок **Создать каталог для решения** .  
  
5.  Примите расположение по умолчанию или нажмите кнопку **Обзор** , чтобы выбрать папку.  
  
6.  В диалоговом окне **Расположение проекта** выберите папку и нажмите кнопку **Открыть**.  
  
7.  Нажмите кнопку **ОК**.  
  
8.  По умолчанию будет создан пустой пакет с именем Package.dtsx, который будет добавлен к проекту. Однако вы не будете использовать этот пакет, вместо этого нужно добавить в проект существующий пакет. Поскольку будут развернуты все пакеты в проекте, следует удалить файл Package.dtsx. Чтобы удалить файл, щелкните его правой кнопкой мыши и выберите пункт **Удалить**.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Шаг 3. Добавление пакетов и других файлов](../integration-services/lesson-1-3-adding-packages-and-other-files.md)  
  
![Значок Integration Services (маленький)](media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Проекты служб Integration Services (SSIS)](integration-services-ssis-projects-and-solutions.md)  
  
  
