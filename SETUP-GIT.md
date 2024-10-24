1: Chuẩn bị
    1.1: github - https://github.com/new - git clone git@github.com:TrongTrinh/Angular-setup.git
    1.2: Basic code Angular: ng new Angular-setup
    1.3: Tạo Branch: git checkout -b dev
    1.4: Tạo Branch: set-format-validation
2: Setup Eslint, Prettier, Husky, commitlint sử dụng trong Angular
    2.1: Links
        2.1.1: Commitlint Angular: https://github.com/conventional-changelog/commitlint/blob/master/%40commitlint/config-angular/README.md
    2.2: Hướng dẫn cài đặt
        2.2.1: Eslint:  ng add @angular-eslint/schematics
        2.2.2: Prettier + Eslint Prettier: 
            - yarn add  prettier prettier-eslint eslint-config-prettier eslint-plugin-prettier -D
            - Update file eslint.config.js: 
                const eslintPluginPrettierRecommended = require('eslint-plugin-prettier/recommended');
                extends: [ eslintPluginPrettierRecommended  ]
            - Add file: .prettierrc.json
                {
                  "tabWidth": 2,
                  "useTabs": false,
                  "singleQuote": true,
                  "semi": true,
                  "bracketSpacing": true,
                  "arrowParens": "avoid",
                  "trailingComma": "es5",
                  "bracketSameLine": true,
                  "printWidth": 80,
                  "overrides": [
                    {
                      "files": "*.html",
                      "options": {
                        "parser": "angular"
                      }
                    }
                  ]
                }
            - Chạy: rm -rf node_modules yarn.lock  để xoá version cũ
            - Thêm dòng: "lint:fix": "prettier --write src && ng lint --fix" vào package.json scripts => chạy yarn lint:fix để fix tất cả code theo format, validate eslint + prettier
        - Husky + lint staged - Chặn đẩy code format sai lên git
            - yarn add husky lint-staged -D & npx husky-init
            - File pre-commit:
                #!/usr/bin/env sh
                . "$(dirname -- "$0")/_/husky.sh"

                npx lint-staged

            - File package json
              "lint-staged": {
                          "src/**/*.{js,ts,html,css,scss}": [
                            "prettier --write",
                            "eslint --max-warnings=0"
                          ]
                        }

            - (Chạy npx lint-staged để thấy kết quả)
            - Check thêm tổng số lượng file
        - Husky + Commintlint
            - yarn add @commitlint/config-angular @commitlint/cli -D
            - Tạo file commitlint.config.js: 
                  echo "module.exports = { extends: ['@commitlint/config-angular'] };" > commitlint.config.js
            - Husky check commit message trước khi đẩy code lên git:
                  npx husky .husky/commit-msg  'npx --no -- commitlint --edit ${1}'
            - Commitlint với scope bắt buộc + format scope: ID-<number>
                module.exports = {
                  extends: ["@commitlint/config-angular"],
                  rules: {
                    "scope-enum": [2, "always", [/^ID-\d+$/]],
                    "scope-case": [2, "always", "pascal-case"],
                    "scope-empty": [2, "never"],
                  },
                };
            - Thêm "no-console": "error", vào eslint config rules để chặn console

3: Thông tin khác
    - ESLint:
        - Mục đích: Xác định và sửa các vấn đề trong mã JavaScript của bạn.
        - Lợi ích: Giúp duy trì phong cách mã nhất quán, phát hiện lỗi tiềm ẩn sớm và áp dụng các tiêu chuẩn mã hóa.
    - Prettier:
        - Mục đích: Tự động định dạng mã của bạn để đảm bảo phong cách nhất quán.
        - Lợi ích: Tiết kiệm thời gian trong việc xem xét mã, giảm tranh cãi về định dạng mã và đảm bảo tất cả mã trông giống nhau bất kể ai viết.
    - Husky:
        - Mục đích: Quản lý các Git hooks để chạy các script trước khi thực hiện các hành động Git nhất định (ví dụ: commit, push).
        - Lợi ích: Đảm bảo rằng các kiểm tra chất lượng mã (như linting và tests) được chạy trước khi mã được commit, ngăn chặn mã xấu vào kho lưu trữ.
    - Commitlint:
        - Mục đích: Áp dụng định dạng thông điệp commit nhất quán.
        - Lợi ích: Giúp dễ dàng đọc và hiểu lịch sử dự án, cải thiện chất lượng thông điệp commit và hỗ trợ tự động hóa quy trình phát hành bằng các công cụ như semantic-release.
    - lint-staged:
        - Mục đích: Chạy các linter trên các file đã được staged trước khi commit.
        - Lợi ích: Đảm bảo rằng chỉ các file được commit mới được lint, giúp tăng tốc quá trình và đảm bảo rằng tất cả mã được commit đều đáp ứng các tiêu chuẩn của dự án.

