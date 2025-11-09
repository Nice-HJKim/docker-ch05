FROM python:3.11.9

# 컨테이너 내 작업 디렉터리
WORKDIR /usr/src/app

# 먼저 requirements.txt만 복사 (빌드 캐시 최적화)
COPY requirements.txt .

# pip 최신화 & 라이브러리 설치
RUN python -m pip install --upgrade pip \
    && pip install -r requirements.txt

# 그다음 나머지 프로젝트 파일 복사
COPY . .

# myapp 디렉토리로 이동
WORKDIR /usr/src/app/myapp

# 포트 노출
EXPOSE 8000

# 운영용: Gunicorn 실행 (exec 형식)
CMD ["gunicorn","--bind","0.0.0.0:8000","myapp.wsgi:application"]

# 개발용(runserver)로 바꾸고 싶을 땐 위 CMD 대신 아래 한 줄만 사용
# CMD ["python","manage.py","runserver","0.0.0.0:8000"]
