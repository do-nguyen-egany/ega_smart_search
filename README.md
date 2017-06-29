# ega_smart_search
Chức năng search auto suggest cho site bizweb, kế thừa từ shopify_smartsearch của `tu.nguyen`

## Nâng cấp từ shopify_smartsearch
- sử dụng Rxjs để giảm số lượng request tới server và kết quả không bị giựt giựt nhảy nhảy

## Demo
- http://ega-bach-hoa.bizwebvietnam.net/

## Yêu cầu
- jquery, requirejs, Rxjs 

## Cài đặt
- tải file `search.json.bwt` vào thư mục `templates`
- tải file `smart-search.bwt` vào thư mục `snippets`
- tải file `rx.all.min.` vào thư mục `assets`

## Gắn vào site
- `{% include 'smart-search' %}` vào file `layouts/theme.bwt`
- ở file require-config thêm khai báo:

`{% assign rx = 'rx.all.min.js' | asset_url %}`

`{% unless rx contains '?' %} {% assign rx =  'rx.all.min' | asset_url %} {% endunless %}`

`
requirejs.config({
    paths:
        {
            ...
            Rx: "{{ rx }}"
        },
    shim:
        {
            ...
            Rx:{
                deps: [],
                exports: 'Rx'
            }
        }
})

`

## Settings
- `settings.display_suggest_search_article`: type = chebox
- `settings.suggest_result_count`: type = text
- `settings.display_suggest_search_description`: type = chebox
