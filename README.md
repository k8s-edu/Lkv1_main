# Lkv1_main — 쿠버네티스 강의 v1 Helm Chart Repository

쿠버네티스 강의 생태계 v1을 위한 Helm chart 저장소입니다.  
GitHub Pages를 통해 Helm chart를 배포합니다.

---

## 사용법

강의 환경에 맞는 Kubernetes 버전의 repo를 추가합니다.

```bash
# Kubernetes 1.35 환경 (cicd 강의)
helm repo add edu https://k8s-edu.github.io/Lkv1_main/helm-charts/v1.35/cicd/
helm repo update
```

---

## 제공 Chart 목록

### cicd — CI/CD 강의용

| K8s 버전 | Chart | App 버전 | Chart 버전 | Helm repo 경로 |
|---|---|---|---|---|
| v1.30 | Jenkins | 2.440.3 | 5.1.12 | `helm-charts/v1.30/cicd/` |
| v1.30 | Argo CD | v2.11.0 | 6.9.0 | `helm-charts/v1.30/cicd/` |
| **v1.35** | **Jenkins** | **2.541.3** | **5.2.0** | **`helm-charts/v1.35/cicd/`** |
| **v1.35** | **Argo CD** | **v3.4.2** | **9.5.14** | **`helm-charts/v1.35/cicd/`** |

---

## 저장소 구조

```
main 브랜치 (Chart 소스)
└── helm-charts/
    ├── v1.30/
    │   └── cicd/
    │       ├── jenkins/     ← Jenkins Helm chart 소스
    │       └── argo-cd/     ← Argo CD Helm chart 소스
    └── v1.35/
        └── cicd/
            ├── jenkins/
            └── argo-cd/

gh-pages 브랜치 (GitHub Pages 서빙)
└── helm-charts/
    ├── v1.30/cicd/
    │   ├── jenkins-5.1.12.tgz
    │   ├── argo-cd-6.9.0.tgz
    │   └── index.yaml
    └── v1.35/cicd/
        ├── jenkins-5.1.12.tgz
        ├── argo-cd-6.9.0.tgz
        └── index.yaml
```

## Chart 업데이트 방법

1. `main` 브랜치에서 해당 버전 경로의 `Chart.yaml` 수정
2. `helm package helm-charts/<k8s-ver>/cicd/<chart>/` 로 `.tgz` 생성
3. `gh-pages` 브랜치 checkout
4. 생성된 `.tgz`를 해당 경로에 복사
5. `helm repo index helm-charts/<k8s-ver>/cicd/ --merge helm-charts/<k8s-ver>/cicd/index.yaml` 로 index 갱신
6. `gh-pages` 브랜치에 commit + push

---

## 관련 저장소

| 저장소 | 용도 |
|---|---|
| [sungmincs/_Lecture_cicd_learning.kit](https://github.com/sungmincs/_Lecture_cicd_learning.kit) | CICD 강의 실습 키트 (이 repo의 Helm chart 사용) |
| [k8s-edu/helm-charts](https://github.com/k8s-edu/helm-charts) | Helm chart 원본 소스 |
