<p>
  OpenAI Speech-To-Text service for the Freeswitch. <br>
  Features: vad, cmd api, flexible settings. <br>
  A small installation guide can be found here: <a href="https://github.com/aks-devs/mod_openai_asr/issues/1">Fail to compile module</a>
</p>

### Dialplan example
```XML
<extension name="openai-asr">
  <condition field="destination_number" expression="^(3222)$">
    <action application="answer"/>
    <action application="play_and_detect_speech" data="/tmp/test2.wav detect:openai"/>
    <action application="sleep" data="1000"/>
    <action application="log" data="CRIT SPEECH_RESULT=${detect_speech_result}"/>
    <action application="hangup"/>
 </condition>
</extension>
```

### mod_quickjs
```javascript
session.ttsEngine= 'openai'; // requires: mod_openai_tts
session.asrEngine= 'openai';

var txt = session.sayAndDetectSpeech('Hello, how can I help you?', 10);
consoleLog('info', "TEXT: " + txt);
```

### Command line
```
freeswitch> openai_asr_transcript /tmp/test.[wav|mp3] [key=altKey mode=altModel]
+OK: How old is the Brooklyn Bridge
```
