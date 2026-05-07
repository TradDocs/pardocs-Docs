# ParDocs

ParDocs API 문서 사이트입니다. Mintlify 기반으로 작성되었으며 Vercel로 배포됩니다.

## 로컬 개발

[Mintlify CLI](https://www.npmjs.com/package/mintlify)를 설치합니다.

```bash
npm i -g mintlify
```

프로젝트 루트(`mint.json` 위치)에서 실행합니다.

```bash
mintlify dev
```

## 배포 구조

**정적 파일 기반 Vercel 배포**를 사용합니다.

- `export.zip` — Mintlify CLI로 로컬에서 생성한 정적 사이트 (구버전 디자인 유지)
- Vercel이 빌드 시 `export.zip`을 압축 해제하여 `dist/`를 생성하고 서빙

### Vercel 설정

| 항목 | 값 |
|---|---|
| Build Command | `unzip -o export.zip -d dist` |
| Output Directory | `dist` |

`vercel.json`에도 `outputDirectory: dist`가 명시되어 있습니다.

### 문서 내용 수정 후 배포 방법

1. `.mdx` 파일 수정
2. 로컬에서 `export.zip` 재생성:
   ```bash
   mintlify export
   ```
3. 생성된 `export.zip`을 커밋하고 push
4. Vercel이 자동으로 재배포

## 트러블슈팅

- `mintlify dev` 실행 안됨 → `mintlify install` 실행
- 페이지 404 → `mint.json`이 있는 폴더에서 실행 중인지 확인
