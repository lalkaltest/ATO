# ATO
ATO+rate lbmit bypass


1. Добавлять новый параметр &email=
2. OTP брутфорсе/recovery code bruteforcing/токены, смотреть также предугадываемые они или нет (https://hackerone.com/reports/691698)
3. Использовать токены/ссылки/коды с одного мыла/юзера/телефона для другого мыла/юзера/телефона (https://medium.com/@ravillabharath123/account-take-over-without-user-interaction-f4ed2bf977de)
4. Менять хост в запросе на сброс пароля(https://medium.com/@swapmaurya20/password-reset-poisoning-leading-to-account-takeover-f178f5f1de87)
5. Через CSRF а настройках аакаунта - поменять мыло на мыло атакующего/пароль Возможно нужно чистое мыло, не зареганное в сервисе, или наоборот. Если есть токен - использовать произвольный или просто удалять его.(https://hackerone.com/reports/6910 https://hackerone.com/reports/538800)
6. Менять POST на GET при всех тестах
7. Пробовать регать аккаунты на уже зареганые мыла,телефоны (https://medium.com/@bathinivijaysimhareddy/tale-of-account-takeovers-part-2-9abf62de4ca3)
8. Если логин:пароль хранятся в куках, то нужна XSS - обращать внимание на куки, например можно поменяь в куках свое ID на ID жертвы и обновиь страницу браузера(https://hackerone.com/reports/215859)
9. Обращать внимание как формирует код/токен, слабый ли он и можно его предугадать(https://medium.com/@bathinivijaysimhareddy/tale-of-account-takeovers-part-2-9abf62de4ca3 последний сценарий)
10. Угон аккаунта через регитсрацию на тоже мыло с хистростью, например adc@mail.ru и adc@mail.ru%0a в запросе. который перехватывается на лету(https://medium.com/hackcura/multiple-flaws-leads-to-account-takeover-within-an-application-9f64abfb1073)
11. При восстановлении пародя менять мыло атакующего в на мыло жертвы в запросе.
____________________________
12. Угон аккаунта при коннекте других акааунтов в настройке, профиля, типа Yahoo, Github(https://hackerone.com/reports/542047) и других почт, короче THIRD-PARTY сервисы или при логине через THIRD-PARTY сервисы(https://hackerone.com/reports/423022 https://hackerone.com/reports/46333 0https://hackerone.com/reports/240821)

1. Create 2 Account With Email
Account X-1 : Attacker
Account X-2 : Victim
2. Sign In To Account X-1 And Go To https://zeit.co/account And Click On Connect with Github And click on authorize ... ( On github )
3. And Intercept The Request And Copy The Value Of Parameter code

https://zeit.co/api/now/registration/github-callback?code=Value&state=
4. Sign In To Account X-2 And Go To https://zeit.co/api/now/registration/github-callback?code=Value&state=
5. And You Can ( Attacker X-1 ) sign in to Account x-2 ( victim ) via Sign in with Github
______________________________________
13. Меняем хост при входе в акааунт через другой сервис attacker.com/victim.com (https://hackerone.com/reports/317476)
14. Как у и случае с CSRF, удалять или менять токен при восстановлении(https://hackerone.com/reports/544334)
15. Смежные проблемы с SMS кодами(https://blog.deteact.com/ru/common-flaws-of-sms-auth/)
17. При подписке/сабскрайбе, смотреть запрос и пробовать манипулировать параметрами (https://hackerone.com/reports/394329)
18. Обращать вниманеи на IDOR, например при смене пароля(https://hackerone.com/reports/751281)
19. CSRF при изменении пароля в личном кабинете(https://hackerone.com/reports/152052)
19. Обращать внимание на CORS, если возвращаются какие-то инетресные данные(https://hackerone.com/reports/685032 https://hackerone.com/reports/426147)
20. Тестить два аккаунта, и пробовать регать снова на неподтвержденную еще почту. Объеденять это с другими методами. например смотреть THIRD-PARTY cервисы(https://hackerone.com/reports/761655)
21. Open redirect при регистарции позволяет спизидть токен, если направить на свой домен (https://hackerone.com/reports/541701)
22. СSRF при добалении/прилинковке THIRD-PERTY сервиса для логина, наприме Фейсбука(https://hackerone.com/reports/235642)
23. Кликджекинг/clickjacking в настройках в кабенете, где можно заставить бзвепря помепнять пароль/мыло (https://hackerone.com/reports/261652)
24. При поиске багов типа АТО или обхода смс кодов, всегда иметь два разных аккаунта зареганных с двумя разными номерами телеыона. Потом юзать токены, пароли, смс коды от одного акаунта на другом, если например кода одинаковые приходят
25. Обращать внимание на Open Redirect в поста запросах, которые находят в механизмах/запросах логина, может привести к ATO(https://noobe.io/articles/2020-06/unvalidated-redirect-parameter-tampering-acc-takeover)
26. При опен редиректе, чтобы спиздить токен, тестить IDN homograph attack (https://hackerone.com/reports/861940)
27. Try sending blank OTP code. Remove the value of OTP parameter.
How I test for bugs in password reset functionality: (https://medium.com/@fatnassifiras45/how-i-was-able-to-take-over-any-account-via-the-password-reset-functionality-ef1659f8b481)
28. Менять отрицательный ответ сервера на положительный, предварительно изучив/перехватив оба в Бурс Суите(https://medium.com/swlh/tale-of-multiple-account-takeover-on-single-platform-19c019b1d1cb)


    I change the host when sending the request.
    I look for the token in the response.
    Tamper with id/email params if available (Add them if not).
    I collect a good number of tokens and analyze them by asking questions like this:
    Can it be decoded?
    Is it bruteForcable?
    Is it predictable?
    What part of the token remains the same?

ATO используя свой ngrok (https://medium.com/@dheerajkmadhukar/do-it-asap-9d1847472bc8) https://target.com@ngrok.com/

При тестировании повышения привилегий использовать маркер, например 1337, чтобы в бурпе потом искать запросы по маркеры и пробовать повторять
Обход 2FA - отключать хидеры капчи(https://shivangx01b.github.io/2fa_bypass/)

2FA Bypass:-

1) Create account and enable 2FA.
2) Now just logout from the account.
3)Reset the password for the account.
4)You will get the dashboard .

2FA Bypass: смотри 2FAbypass.png в папке тест

https://www.anugrahsr.me/posts/10-Password-reset-flaws/

Rate LImit bypass https://medium.com/bugbountywriteup/bypassing-rate-limit-like-a-pro-5f3e40250d3c

Tip :- Always try to add another header like - "X-Forwarded-Host" in the Password reset request.

Rate limit bypass (https://princej-76.medium.com/bypassed-rate-limit-2-7b409c58161) Добавление символа %00 %00%00 и так далее к телеофну и можно например зарегать кучу аккаунтов на один тел
_________________________________

OTP bypas (https://mokhansec.medium.com/account-verification-code-bypass-lead-to-a-4000-bounty-b31dda6f3011)

The request was a POST request and the content type is application/JSON. I read it somewhere that you can use an Array to bypass OTP verification. Like this (let day the valid OTP was 1337)

{
"otp":[
"1234",
"1111",
"1337",
"2222",
"3333",
"4444",
"5555"]
}
