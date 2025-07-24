    <!-- Header Section -->
    <div id="header-placeholder"></div>
    <script>
        fetch('header.html')
            .then(res => res.text())
            .then(html => {
                document.getElementById('header-placeholder').innerHTML = html;
            })
            .catch(err => console.error('Failed to load header page: ', err));
    </script>


  <!-- Back to Top Button -->
  <button id="back-to-top"
    class="back-to-top fixed bottom-8 right-8 w-12 h-12 rounded-full bg-gradient-to-r from-primary to-secondary flex items-center justify-center shadow-lg z-50 transition-all duration-300">
    <div class="w-6 h-6 flex items-center justify-center">
      <i class="ri-arrow-up-line text-black"></i>
    </div>
  </button>


    <!-- Footer -->
    <div id="footer-placeholder"></div>
    <script>
        fetch('footer.html')
            .then(res => res.text())
            .then(html => {
                document.getElementById('footer-placeholder').innerHTML = html;
            })
            .catch(err => console.error('Failed to load footer page: ', err));
    </script>



    <!-- for header action -->
    <script id="global-event-delegation">
        document.body.addEventListener('click', e => {
            // 移动菜单切换
            if (e.target.closest('#mobile-menu-button')) {
                document.querySelector('#mobile-menu').classList.toggle('hidden');
            }
            // 语言下拉切换
            if (e.target.closest('.language-selector > button')) {
                document.querySelector('.language-options').classList.toggle('hidden');
            }
            // 选择语言
            const opt = e.target.closest('.language-option');
            if (opt) {
                const lang = opt.dataset.lang;
                ['en', 'zh', 'ja'].forEach(l => {
                    document.querySelectorAll('.lang-' + l)
                        .forEach(el => el.classList.toggle('hidden', l !== lang));
                });
                // 更新当前语言显示
                document.querySelectorAll('.current-language')
                    .forEach(el => {
                        el.textContent = opt.textContent;
                    });
                // 用 class 收起下拉
                document.querySelector('.language-options')
                    .classList.add('hidden');
            }
        });
    </script>
