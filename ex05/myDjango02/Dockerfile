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
CMD gunicorn --bind 0.0.0.0:8000 myapp.wsgi:application

# 포트 노출
EXPOSE 8000

# 개발 서버 실행 (실습용)
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]

