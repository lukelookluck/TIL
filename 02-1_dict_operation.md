```python
from pprint import pprint

ssafy = {
    'location': ['서울', '대전', '구미', '광주'],
    'language': {
        'python': {
            'python standard library': ['os', 'random', 'webbrowser'],
            'frameworks': {
                'flask': 'micro',
                'django': 'full-functioning'
            },
            'data_science': ['numpy', 'pandas', 'scipy', 'sklearn'],
            'scraping': ['requests', 'bs4'],
        },
        'web' : ['HTML', 'CSS']
    },
    'classes': {
        'gm': {
            'lecturer': 'justin',
            'manager': '김아름',
            'class president': '박지은',
            'groups': {
                'A': ['이상준', '김민지', '이종우', '강성묵', '박현수'],
                'B': ['홍세진', '이지훈', '주재성', '김태인', '문종혁'],
                'C': ['유수정', '신경제', '김영주', '임준성'],
                'D': ['유건우', '홍연주', '임창묵', '양진엽'],
                'E': ['김지영', '도정우', '황영준', '안시경', '황신실']
            }
        },
        'gj': {
            'lecturer': 'change',
            'manager': 'pro-gj'
        }
    }
}
```


```python
"""
난이도* 1. 지역(location)은 몇 개 있나요?
출력예시)
4
"""
```




    '\n난이도* 1. 지역(location)은 몇 개 있나요?\n출력예시)\n4\n'




```python
len(ssafy['location'])
```




    4




```python
"""
난이도** 2. python standard library에 'requests'가 있나요?
출력예시)
False
"""
```




    "\n난이도** 2. python standard library에 'requests'가 있나요?\n출력예시)\nFalse\n"




```python
'request' in ssafy['language']['python']['python standard library']
```




    False




```python
"""
난이도** 3. gm 반의 반장의 이름을 출력하세요.
출력예시)
박지은
"""
```


```python
print(ssafy['classes']['gm']['class president'])

```

    박지은
    


```python
"""
난이도*** 4. ssafy에서 배우는 언어들을 출력하세요.
출력 예시)
python
web
"""
```


```python
###
for lang in ssafy['language'].keys():
    print(lang)
```

    python
    web
    


```python
"""
난이도*** 5 ssafy gj반의 강사와 매니저의 이름을 출력하세요.
출력 예시)
change
pro-gj
"""
```


```python
for name in ssafy['classes']['gj'].values():
    print(name)
```

    change
    pro-gj
    


```python
"""
난이도***** 6. framework 들의 이름과 설명을 다음과 같이 출력하세요.
출력 예시)
flask는 micro이다.
django는 full-functioning이다.
"""
```


```python
for name, des in ssafy['language']['python']['frameworks'].items():
    print(f'{name}는 {des}이다.')
```

    flask는 micro이다.
    django는 full-functioning이다.
    


```python
"""
난이도***** 7. 오늘 당번을 뽑기 위해 groups의 E 그룹에서 한명을 랜덤으로 뽑아주세요.
출력예시)
오늘의 당번은 주재성
"""
```


```python
import random
names = ssafy['classes']['gm']['groups']['E']
result = random.choice(names)

print(result)
```

    안시경
    
