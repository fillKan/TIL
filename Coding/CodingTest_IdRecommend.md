# 2021 카카오 코딩 테스트 1번

> **신규 아이디 추천**
>
> '카카오에 입사한 신입 개발자 `네오`는 "카카오계정개발팀"에 배치되어, 카카오 서비스에 가입하는 유저들의 아이디를 생성하는 업무를 담당하게 되었습니다. "네오"에게 주어진 첫 업무는 새로 가입하는 유저들이 카카오 아이디 규칙에 맞지 않는 아이디를 입력했을 때, 입력된 아이디와 유사하면서 규칙에 맞는 아이디를 추천해주는 프로그램을 개발하는 것입니다.'
>
> https://programmers.co.kr/learn/courses/30/lessons/72410

```c++
#include <iostream>
#include <string>
#include <vector>

using namespace std;

inline bool IsChar(char c)
{
	return (int)c >= 65 && (int)c <= 92 
		|| (int)c >= 97 && (int)c <= 122;
}
inline bool IsNumber(char c) {
	return (int)c >= 48 && (int)c <= 57;
}
inline void Small2Big(char& c) 
{
	c += (int)c >= 65 && (int)c <= 92 ? (char)32 : (char)0;
}
void TrimString(string& s)
{
	for (size_t i = 0; i < s.size(); i++)
	{
		if (!IsChar(s[i]) && !IsNumber(s[i]))
		{
			if (s[i] != '.' && s[i] != '_' && s[i] != '-')
			{
				s.erase(i--, 1);
			}
		}
	}
	{
		int i = 0;
		while (s.size() > i + 1)
		{
			if (s[i] == '.' && s[i + 1] == '.')
			{
				s.erase(i, 1);
			}
			else
			{
				i++;
			}
		}
	}
	if (s[0] == '.')
	{
		s.erase(0, 1);
	}
	if (s.size() > 1) 
	{
		if (s[s.size() - 1] == '.')
		{
			s.erase(s.size() - 1, 1);
		}
	}
	if (s.size() == 0) 
	{
		s = "a";
	}
	if (s.size() >= 16) 
	{
		s.erase(s.begin() + 15, s.end());
	}
	if (s.size() > 1)
	{
		if (s[s.size() - 1] == '.')
		{
			s.erase(s.size() - 1, 1);
		}
	}
	if (s.size() < 3) 
	{
		char push = s.back();

		while (s.size() < 3) {
			s.push_back(push);
		}
	}
}

string Solution(string new_id)
{
	char idBuffer = ' ';
	string answer = "";

	for (size_t i = 0; i < new_id.size(); i++) 
	{
		Small2Big(new_id[i]);
		answer.push_back(new_id[i]);
	}
	TrimString(answer);
	return answer;
}
```

