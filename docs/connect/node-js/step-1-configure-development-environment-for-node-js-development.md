---
title: "Шаг 1: Настройка среды разработки для разработки приложений Node.js | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: node-js
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dad01f1-fadf-4ac9-9b4d-26be3d301886
caps.latest.revision: "17"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 7d723913fbc63e65a28031421da004e942f49f6e
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="step-1--configure-development-environment-for-nodejs-development"></a>Шаг 1: Настройка среда разработки для Node.js
Необходимо будет настроить среду разработки с необходимых компонентов для разработки приложений с помощью драйвера Node.js для SQL Server.  Наиболее распространенный метод является использование диспетчера пакетов node (npm-файл) для установки трудоемкой модуля, но вы можете скачать модуль трудоемкой непосредственно в [Github](https://github.com/pekim/tedious) при необходимости.  
  
Обратите внимание, что драйвер Node.js использует протокол потока табличных данных, включенный по умолчанию в SQL Server и базы данных SQL Azure.  Дополнительная настройка не требуется.  
  
## <a name="windows"></a>Windows  
  
1. **Установка диспетчера пакетов среды выполнения и npm Node.js**  
а. Последовательно выберите пункты [Node.js](https://nodejs.org/en/download/)  
б. Щелкните соответствующую ссылку MSI-файл установщика Windows.   
в. После загрузки, запустите MSI-файл для установки Node.js  
  
2. **Откройте cmd.exe**  
  
3. **Создайте каталог проекта** и перейти в эту папку.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
4. **Создание проекта узла.**  Чтобы сохранить значения по умолчанию при создании вашего проекта, нажмите клавишу ВВОД, пока не будет создан проект. В конце этого шага вы должны увидеть файла package.json в каталоге проекта.  
```  
> npm init  
```  
  
5. **Установите модуль трудоемкой в своем проекте.**  Это реализация протокола TDS, использующего драйвер для связи с SQL Server.  
```  
> npm install tedious  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1.  **Откройте терминалов**  
  
2. **Установка среды выполнения Node.js**  
```  
>sudo apt-get install node  
```  
3. **Установка npm (узел диспетчера пакетов)**  
```  
> sudo apt-get install npm  
```  
4. **Создайте каталог проекта** и перейти в эту папку.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
5. **Создание проекта узла.**  Чтобы сохранить значения по умолчанию при создании вашего проекта, нажмите клавишу ВВОД, пока не будет создан проект. В конце этого шага вы должны увидеть файла package.json в каталоге проекта.  
```  
> sudo npm init  
```  
  
6. **Установите модуль трудоемкой в своем проекте.**  Это реализация протокола TDS, использующего драйвер для связи с SQL Server.  
```  
> sudo npm install tedious  
```  
  
## <a name="mac"></a>Mac  
  
1. **Установка диспетчера пакетов среды выполнения и npm Node.js**  
а. Последовательно выберите пункты [Node.js](https://nodejs.org/en/download/)  
б. Щелкните соответствующую ссылку установщика Mac OS.  
в. После скачивания выполните dmg для установки Node.js  
  
2. **Откройте терминалов**  
  
3. **Создайте каталог проекта** и перейти в эту папку.    
```  
> mkdir HelloWorld  
> cd HelloWorld  
```  
  
4. **Создание проекта узла.**  Чтобы сохранить значения по умолчанию при создании вашего проекта, нажмите клавишу ВВОД, пока не будет создан проект. В конце этого шага вы должны увидеть файла package.json в каталоге проекта.  
```  
> npm init  
```  
  
5. **Установите модуль трудоемкой в своем проекте.**  Это реализация протокола TDS, использующего драйвер для связи с SQL Server.  
```  
> npm install tedious  
```  
  
