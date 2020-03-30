---
title: Шаг 1. Настройка среды разработки pymssql в Python | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6d392a5e-b08e-4b35-9e99-61260888fc41
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5bf2942b79cf7e72efbb36a53019de8208cd3b8e
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67935825"
---
# <a name="step-1-configure-development-environment-for-pymssql-python-development"></a>Шаг 1. Настройка среды разработки для разработки на Python в pymssql
Чтобы разработать приложение с помощью драйвера Python для SQL Server, необходимо настроить среду разработки, учитывая необходимые условия.    
  
Обратите внимание, что драйверы Python SQL используют протокол TDS, включенный по умолчанию в SQL Server и Базу данных SQL Azure.  Дополнительная настройка не требуется.  
  
## <a name="windows"></a>Windows  
  
1. **Установите среду выполнения Python и диспетчер пакетов PIP**  
а. Перейдите на [Python.org](https://www.python.org/downloads/)  
b. Нажмите на соответствующую ссылку установщика msi Windows.   
c. После загрузки запустите msi, чтобы установить среду Python.  
  
2. **Загрузите модуль pymssql** [здесь](https://www.lfd.uci.edu/~gohlke/pythonlibs/#pymssql)  
  
    Убедитесь, что выбран правильный файл WHL.  Например: если вы используете Python 2.7 на 64-разрядном компьютере, выберите файл pymssql‑2.1.1‑cp27‑none‑win_amd64.whl. После загрузки файла WHL разместите его в папке C:/Python27.  
      
3. **Откройте cmd.exe**  
  
4. **Установите модуль pymssql**     
    Например, если вы используете Python 2.7 на 64-разрядном компьютере:  
```  
> cd c:\Python27  
> pip install pymssql‑2.1.1‑cp27‑none‑win_amd64.whl  
```  
  
## <a name="ubuntu-linux"></a>Ubuntu Linux  
  
1. **Установите среду Python и диспетчер пакетов PIP**. Python поставляется предустановленным на большинстве дистрибутивов Ubuntu.  Если на вашем компьютере не установлен Python, вы можете либо скачать исходный архив tarball с [python.org](https://www.python.org/downloads/) и собрать его локально, либо воспользоваться диспетчером пакетов:  
```  
> sudo apt-get install python   
```  
  
2.  **Откройте терминал**  
  
3.  **Установите модуль и зависимости pymssql**  
```  
> sudo apt-get --assume-yes update  
> sudo apt-get --assume-yes install freetds-dev freetds-bin  
> sudo apt-get --assume-yes install python-dev python-pip  
> sudo pip install pymssql  
```  
  
## <a name="mac"></a>Mac  
  
1. **Установите среду выполнения Python и диспетчер пакетов PIP**  
а. Перейдите на [Python.org](https://www.python.org/downloads/)  
b. Щелкните ссылку на соответствующий установщик pkg Mac.   
c. После загрузки запустите pkg, чтобы установить среду Python.  
  
2.  **Откройте терминал**  
  
3. **Установите диспетчер пакетов Homebrew**  
```  
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"  
```  
  
4.  **Установите модуль FreeTDS**  
```  
> brew install FreeTDS  
```  
  
5.  **Установите модуль pymssql**  
```  
> sudo -H pip install pymssql  
```
