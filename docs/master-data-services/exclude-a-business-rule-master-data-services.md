---
title: "Исключение бизнес-правила (службы Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "бизнес-правила [службы Master Data Services], исключение"
ms.assetid: bdbc9df0-23f7-40b9-8aba-4445c1482580
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Исключение бизнес-правила (службы Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]исключите бизнес-правило, если его не следует удалять без возможности восстановления и отсутствует необходимость проверки данных на соответствие этому бизнес-правилу.  
  
## Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
### Исключение бизнес-правила  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  В строке меню выберите **Управление** и щелкните **Бизнес-правила**.  
  
3.  На странице **Бизнес-правила** в раскрывающемся списке **Модель** выберите модель.  
  
4.  Из раскрывающегося списка **Сущность** выберите сущность.  
  
5.  Из раскрывающегося списка **Типы элементов** выберите тип элемента.  
  
6.  В сетке выберите строку бизнес-правила, которое необходимо исключить, и щелкните **Изменить**.  
  
7.  Установите флажок **Исключено**.  
  
8.  Нажмите кнопку **Сохранить**.  
  
9. Нажмите кнопку **Опубликовать все**.  
  
10. В диалоговом окне подтверждения нажмите кнопку **ОК**. В столбце **Business Rule Status** (Состояние бизнес-правила) указано значение **Исключено** , а в столбце **Исключено** — значение **Да**.  
  
## См. также:  
 [Удаление бизнес-правила (службы Master Data Services)](../master-data-services/delete-a-business-rule-master-data-services.md)   
 [Создание и публикация бизнес-правила (службы Master Data Services)](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)   
 [Бизнес-правила (службы Master Data Services)](../master-data-services/business-rules-master-data-services.md)  
  
  