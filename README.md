# stepik---auto-tests-course
course homework
https://stepik.org/course/72884/promo

from selenium import webdriver
import time
import math


def calc(x):
    return str(math.log(abs(12*math.sin(x))))

try:
    link = "http://SunInJuly.github.io/execute_script.html"
    browser = webdriver.Chrome()
    browser.get(link)

    x_element = browser.find_element_by_css_selector("#input_value")
    x = x_element.text
    y = calc(int(x))


    input1 = browser.find_element_by_css_selector("#answer")
    input1.send_keys(y)
    option1 = browser.find_element_by_css_selector("#robotCheckbox")
    option1.click()
    option1 = browser.find_element_by_css_selector("#robotsRule")
    browser.execute_script("return arguments[0].scrollIntoView(true);", option1)
    option1.click()
    button = browser.find_element_by_css_selector(".btn.btn-primary")

    button.click()

    time.sleep(1)

finally:
    # ожидание чтобы визуально оценить результаты прохождения скрипта
    time.sleep(10)
    # закрываем браузер после всех манипуляций
    browser.quit()
