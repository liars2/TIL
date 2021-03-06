PywinAuto 라이브러리
------------------

## **경고**
```
이 문서는 제가 이해한 내용을 바탕으로 작성되어 틀린 내용이 기재 되었을 수 있습니다.
PywinAuto에 있는 모든 클래스 모듈을 보여주지 않고 필자가 공부한 모듈만 올리고 있습니다.
```
혹시라도 모든 모듈을 보고싶으시다면 [링크](http://pywinauto.readthedocs.io/en/latest/code/code.html)를 참조하시길 바랍니다.


## 목차
1. Pywinauto 란?
2. Pywinauto의 클래스 트리

### PywinAuto 란?
GUI 환경을 위해 만들어진 파이썬 라이브러리이다.
간단하게 대화상자, 키보드, 마우스와 컨트롤 할 수 있는 라이브러리이다.

### PywinAuto 의 클래스 트리

``` markdown
PywinAuto
|# 기본적인 유저 인풋 모델
├──mouse
|──── click
|──── ...
├──keyboard
|──── sendKeys
|
|# 메인 유저 모듈
├──application
|──── start
|──── connect
|──── kill
├── timings
|──── wait_until_passes
|
|# 컨트롤 레퍼런스
├──controls
|──── hwndwrapper
|────── set_focus
|────── send_keystrokes
|──── controls.menuwrapper
```

## pywinauto.mouse
실제 유저처럼 마우스 이벤트를 모방합니다.

`pywinauto.mouse.click`
</br>특정한 좌표를 클릭합니다.
</br>ex) pywinauto.mouse.click(button='left', coord = (0,0)) # 마우스 왼쪽 클릭

`pywinauto.mouse.double_click`
</br>특정한 좌표를 더블클릭합니다.
</br>ex) pywinauto.mouse.double_click(button='left', coord = (0,0)) # 마우스 왼쪽 두번

`pywinauto.mouse.move`
</br>인자값으로 받은 좌표로 움직입니다.
</br>ex) pywinauto.mouse.move(coord = (0,0)) # 마우스 왼쪽 클릭

`pywinauto.mouse.press`
</br>특정한 좌표를 누릅니다.
</br>ex) pywinauto.mouse.press(button='left', coord = (0,0)) # 마우스 왼쪽 클릭

`pywinauto.mouse.release`
</br>특정한 좌표를 뗍니다.
</br>ex) pywinauto.mouse.release(button='left', coord = (0,0)) # 마우스 왼쪽 클릭

pywinauto.keyboard
------------------------
키보드는 단 한가지 메소드 `sendKeys` 밖에 지원하지 않습니다. 이 메소드는 유니코드 및 특별한 키들을 사용할 수 있습니다.

사용가능한 키 코드들:
``` text
{SCROLLLOCK}, {VK_SPACE}, {VK_LSHIFT}, {VK_PAUSE}, {VK_MODECHANGE},
{BACK}, {VK_HOME}, {F23}, {F22}, {F21}, {F20}, {VK_HANGEUL}, {VK_KANJI},
{VK_RIGHT}, {BS}, {HOME}, {VK_F4}, {VK_ACCEPT}, {VK_F18}, {VK_SNAPSHOT},
{VK_PA1}, {VK_NONAME}, {VK_LCONTROL}, {ZOOM}, {VK_ATTN}, {VK_F10}, {VK_F22},
{VK_F23}, {VK_F20}, {VK_F21}, {VK_SCROLL}, {TAB}, {VK_F11}, {VK_END},
{LEFT}, {VK_UP}, {NUMLOCK}, {VK_APPS}, {PGUP}, {VK_F8}, {VK_CONTROL},
{VK_LEFT}, {PRTSC}, {VK_NUMPAD4}, {CAPSLOCK}, {VK_CONVERT}, {VK_PROCESSKEY},
{ENTER}, {VK_SEPARATOR}, {VK_RWIN}, {VK_LMENU}, {VK_NEXT}, {F1}, {F2},
{F3}, {F4}, {F5}, {F6}, {F7}, {F8}, {F9}, {VK_ADD}, {VK_RCONTROL},
{VK_RETURN}, {BREAK}, {VK_NUMPAD9}, {VK_NUMPAD8}, {RWIN}, {VK_KANA},
{PGDN}, {VK_NUMPAD3}, {DEL}, {VK_NUMPAD1}, {VK_NUMPAD0}, {VK_NUMPAD7},
{VK_NUMPAD6}, {VK_NUMPAD5}, {DELETE}, {VK_PRIOR}, {VK_SUBTRACT}, {HELP},
{VK_PRINT}, {VK_BACK}, {CAP}, {VK_RBUTTON}, {VK_RSHIFT}, {VK_LWIN}, {DOWN},
{VK_HELP}, {VK_NONCONVERT}, {BACKSPACE}, {VK_SELECT}, {VK_TAB}, {VK_HANJA},
{VK_NUMPAD2}, {INSERT}, {VK_F9}, {VK_DECIMAL}, {VK_FINAL}, {VK_EXSEL},
{RMENU}, {VK_F3}, {VK_F2}, {VK_F1}, {VK_F7}, {VK_F6}, {VK_F5}, {VK_CRSEL},
{VK_SHIFT}, {VK_EREOF}, {VK_CANCEL}, {VK_DELETE}, {VK_HANGUL}, {VK_MBUTTON},
{VK_NUMLOCK}, {VK_CLEAR}, {END}, {VK_MENU}, {SPACE}, {BKSP}, {VK_INSERT},
{F18}, {F19}, {ESC}, {VK_MULTIPLY}, {F12}, {F13}, {F10}, {F11}, {F16},
{F17}, {F14}, {F15}, {F24}, {RIGHT}, {VK_F24}, {VK_CAPITAL}, {VK_LBUTTON},
{VK_OEM_CLEAR}, {VK_ESCAPE}, {UP}, {VK_DIVIDE}, {INS}, {VK_JUNJA},
{VK_F19}, {VK_EXECUTE}, {VK_PLAY}, {VK_RMENU}, {VK_F13}, {VK_F12}, {LWIN},
{VK_DOWN}, {VK_F17}, {VK_F16}, {VK_F15}, {VK_F14}
```

연산자:
+ '+': {VK_SHIFT}
+ '^': {VK_CONTROL}
+ '%': {VK_MENU} a.k.a Alt 키

ex) pywimauto.keyboard.sendKeys('A') # A를 보낸다.

pywinauto.application
------------------------
이 어플리케이션 모듈은 유저가 가장 처음으로 써야할 것중 하나다.

어플리케이션을 자동화시키려면 어플리케이션 클래스를 실행시켜야만 한다.</br>
그리고, `Application.start()` 혹은 `Application.connect()` 는 객체를 실행시킨다.

`pywinauto.application.connect`
</br>이미 실행중인 프로세스에 연결합니다.
</br>이 메소드는 인자가 ****kwargs** 이므로 이름을 정해줘야만 합니다.
</br>ex) pywinauto.application.connect(runApp = 'currentRunningProcess.exe')

`pywinauto.application.start`
</br>커맨드 라인을 사용해 어플리케이션을 실행시킵니다.
</br>더 많은 인자를 보고 싶으시면 [링크](http://pywinauto.readthedocs.io/en/latest/code/pywinauto.application.html#pywinauto.application.Application.start)를 참조해주세요
</br>ex)pywinauto.application.start('notepad.exe') # 혹은 PATH를 써도 작동합니다.

`pywinauto.application.kill`
</br>프로세스를 종료시킵니다.
</br>ex) pywinauto.application.kill()

pywinauto.timings
------------------------
GUI 어플리케이션의 동작은 종종 불안정하고 새로운 윈도우가 나타나는 동안 기다려야하거나 존재하는 윈도우가 닫히거나 보이지 않습니다.
<br>Pywinauto는 암암리에 대화상자 실행을 기다릴 수 있습니다.

`pywinauto.timings.wait_until_passes`
<br> timeout, 재실행 간격과 함수를 인자값으로 받고 타임아웃동안 간격대로 재실행시킵니다. 자세한 정보는 [링크](http://pywinauto.readthedocs.io/en/latest/code/pywinauto.timings.html?highlight=wait_until_passes#pywinauto.timings.wait_until_passes)를 참조하세요
<br>ex) pywinauto.timings.wait_until_passes(100, 1, application_name.Exists) # 100초 동안 1초씩 self.Exists 를 실행합니다.

pywinauto.controls.hwndwrapper
----------------------
윈도우 컨트롤을 Wrapping한 것.

`pywinauto.controls.hwndwrapper.set_focus()`
</br> 컨트롤에 초점을 맞춥니다. 윈도우를 중요한 위치에 불러오고 시스템이 제한을 둘 수 있습니다. 부수적인 효과를 막기위해 마우스 커서가 화면 밖으로 없어집니다.
</br>ex) notepad.set_focus()

`pywinauto.controls.hwndwrapper.send_keystrokes`
</br> set_text와 다르게 주어진 인자값을 하나씩 끊어서 입력합니다.
</br>ex) searchBar.send_keystrokes('gorilla') #
