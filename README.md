# 11 câu hỏi phỏng vấn kinh khủng về Git sẽ khiến bạn bật khóc

![11 Painful Git Interview Questions and Answers You Will Cry
On](https://res.cloudinary.com/practicaldev/image/fetch/s--ZdnrNCoZ--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://images.pexels.com/photos/929382/pexels-photo-929382.jpeg%3Fauto%3Dcompress%26cs%3Dtinysrgb%26h%3D350)  
Theo khảo sát mới nhất của developer Stack Overflow, hơn 70%
các developer sử dụng Git, khiến nó trở thành VCS được sử dụng nhiều nhất trên thế giới. Git thường được sử dụng cho cả phát triển phần mềm thương mại và open source, với những lợi ích đáng kể cho các cá nhân, nhóm và doanh nghiệp.

### Q1: Git fork là gì? Sự khác biệt fork, branch và clone là gì?

> Topic: **Git**  
Difficulty: ⭐⭐

  * Một **fork**  là một bản sao remote, phía server của một repository, khác với bản gốc. Một fork không thực sự là một khái niệm của  Git, nó giống một ý tưởng chính trị / xã hội hơn.
  * Một **clone** không phải là một fork; một clone là một bản sao local của một remote repository. Khi bạn sao chép, thực ra là bạn đang sao chép toàn bộ source repository, bao gồm tất cả lịch sử và các nhánh.
  * Một **branch** là một cơ chế để xử lý các thay đổi trong một repository duy nhất để cuối cùng merge chúng với phần còn lại của code . Một branch là một phần của một repository. Về mặt khái niệm, nó đại diện cho một luồng phát triển.

**Source:** [stackoverflow.com](https://stackoverflow.com/questions/3329943/git-branch-fork-fetch-merge-rebase-and-clone-what-are-the-differences/)

### Q2: Sự khác nhau giữa một "pull request" và một "branch" là gì?

> Topic: **Git**  
Difficulty: ⭐⭐

  * Một **branch** chỉ là một phiên bản riêng của code.

  * Một **pull request** là khi ai đó lấy repository, tạo nhánh riêng của họ, thực hiện một số thay đổi, sau đó cố gắng merge nhánh đó vào (đưa thay đổi của họ vào repository code của người khác).

**Source:** [stackoverflow.com](https://stackoverflow.com/questions/19059838/whats-the-difference-between-a-pull-request-and-a-branch)

### Q3: Sự khác nhau giữa "git pull" bà "git fetch" là gì?

> Topic: **Git**  
Difficulty: ⭐⭐

Nói một cách đơn giản, `git pull` thực hiện một `git fetch` theo sau là một `git
merge`.

  * Khi bạn sử dụng `pull`, Git sẽ cố gắng tự động thực hiện công việc cho bạn. **Tùy theo từng hoàn cảnh**,Git sẽ merge mọi commit được pull vào nhánh bạn đang làm việc. `pull` **tự động gộp các commit mà bạn sẽ không cần phải review trước**. Nếu bạn không quản lý chặt chẽ các nhánh của mình, bạn có thể gặp phải các xung đột thường xuyên.

  * Khi bạn `fetch`, Git sẽ thu thập bất kỳ commit nào mà từ nhánh chỉ định mà không có trong branch hiện tại của bạn và **lưu nó trong repository trên local của bạn**. Tuy nhiên, **nó không merge chúng với nhánh hiện tại của bạn**. Điều này đặc biệt hữu ích nếu bạn cần cập nhật repository của bạn, nhưng những thứ đang làm việc có thể bị hỏng nếu bạn cập nhật các file của mình. Để tích hợp các commit vào nhánh master của bạn, bạn sử dụng `merge`.

**Source:** [stackoverflow.com](https://stackoverflow.com/questions/292357/what-is-the-difference-between-git-pull-and-git-fetch)

### Q4: Lam sao để revert về commit trước trong git?

> Topic: **Git**  
Difficulty: ⭐⭐⭐

Giả sử bạn có điều này, trong đó C là con trỏ HEAD của bạn và (F) là trạng thái file của bạn.
```
         (F)
        A-B-C
            ↑
          master

```
  * Để nuke thay đổi trong commit 
  
```
    git reset --hard HEAD~1
```
Bây giờ B là HEAD. Bởi vì bạn đã sử dụng --hard, các file của bạn được reset về trạng thái ở commit B

  * Để hủy bỏ commit nhưng vẫn giữ các thay đổi của bạn:

```
    git reset HEAD~1
```
Bây giờ chúng ta yêu cầu Git di chuyển con trỏ HEAD quay trở lại commit (B) và giữ nguyên các file và `git status` sẽ hiện các thay đổi đã có ở C

  * Để hủy commit nhưng vẫn giữ lại các files và index của bạn

```
    git reset --soft HEAD~1
```        
Khi bạn thực hiện `git status`,bạn sẽ thấy các file cùng với index như trước đó.

**Source:** [stackoverflow.com](https://stackoverflow.com/questions/927358/how-to-undo-the-most-recent-commits-in-git)

### Q5:"git cherry-pick" là gì?

> Topic: **Git**  
Difficulty: ⭐⭐⭐

Câu lệnh git _cherry-pick_ thường được sử dụng để chỉ các commit cụ thể từ một nhánh trong một repository trên một nhánh khác. Thường được sử dụng để chuyển tiếp hoặc back-port các commit từ nhánh bảo trì đến nhánh phát triển.


Điều này trái ngược với các cách khác như merge hay rebase mà thường được áp dụng cho nhiều commit vào 1 nhánh khác.

    
    
    git cherry-pick <commit-hash>
    

**Source:** [stackoverflow.com](https://stackoverflow.com/questions/9339429/what-does-cherry-picking-a-commit-with-git-mean)

### Q6:  Giải thích những ưu điểm của Forking Workflow

> Topic: **Git**  
Difficulty: ⭐⭐⭐

**Forking Workflow** về cơ bản sẽ khác với các luồng làm việc Git khác. Thay vì sử dụng một repository duy nhất phia server để hoạt động như một
"trung tâm" codebase, nó cung cấp cho mỗi developer một repository phía server riêng của họ. "Forking Workflow" thường thấy nhất trong các dự án open soure công khai.

Ưu điểm chính của Forking Workflow là các đóng góp có thể được tích hợp mà không cần mọi người push vào một repository trung tâm duy nhất giúp lịch sử commit của dự án được sạch sẽ. Các developer sẽ push lên các repository phía server của họ, và chỉ người bảo trì dự án có thể push lên repository chính.

Khi các developer sẵn sàng publish một commit local, họ push commit đó lên repository công khai của họ, không phải là repository chính. Sau đó, họ tạo một pull request tới repository chính, cho phép người bảo trì dự án biết rằng bản cập nhật sẵn sàng được tích hợp.

**Source:** [atlassian.com](https://www.atlassian.com/git/tutorials/comparing-workflows/forking-workflow)

### Q7: Sự khác nhau giữaa HEAD, working tree và index, trong Git?

> Topic: **Git**  
Difficulty: ⭐⭐⭐

  * **working tree/working directory/workspace**  là cây thư mục (mã nguồn) của các file mà bạn có thể nhìn thấy và chỉnh sửa.
  * **index/staging area** là một file nhị phân lớn, đơn lẻ trong /.git/index,trong đó liệt kê tất cả các file trong nhánh hiện tại,  sha1 checksum của chúng, time stamps và tên file - nó không phải là một thư mục khác với một bản sao của các file trong đó
  * **HEAD** là một tham chiếu đến commit cuối cùng trong nhánh hiện tại đã được checkout

**Source:** [stackoverflow.com](https://stackoverflow.com/questions/3689838/whats-the-difference-between-head-working-tree-and-index-in-git)

### Q8: Bạn có thể giải thích luông làm việc Gitflow không?

> Topic: **Git**  
Difficulty: ⭐⭐⭐

Luồng làm việc Gitflow sử dụng hai nhánh chạy song song _dài hạn_ để lưu lịch sử của project là `master` và `develop`:

  * **Master** \- luôn sẵn sàng để được phát hành trên LIVE, với mọi thứ được kiểm tra và  phê duyệt đầy đủ (sẵn sàng cho production).

    * **Hotfix** \- Các nhánh bảo trì hoặc "hotfix" được sử dụng để nhanh chóng vá lỗi các bản phát hành production. Các nhánh Hotfix giống như các nhánh phát hành và các nhánh tính năng,trừ khi chúng dựa trên `master` thay vì` develop`.
  

  * **Develop** \- là nhánh để mà tất cả các nhánh tính năng được merge vào và nơi tất cả các test được thực hiện. Chỉ khi mọi thứ được kiểm tra kỹ lưỡng và sửa thì nó mới có thể được merge với `master`

    * **Feature** \- mỗi tính năng mới nên được để ở trong nhánh riêng của nó, nó có thể được push lên nhánh `develop` giống nhánh cha của chúng.


![Gitflow workflow](https://res.cloudinary.com/practicaldev/image/fetch/s--pLQxGakq--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://wac-cdn.atlassian.com/dam/jcr:61ccc620-5249-4338-be66-94d563f2843c/05%2520%282%29.svg%3FcdnVersion%3Dji)

**Source:** [atlassian.com](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)

### Q9: Khi nào  chúng ta nên sử dụng "git stash"?

> Topic: **Git**  
Difficulty: ⭐⭐⭐

Lệnh `git stash` sẽ lấy tất cả các thay đổi chưa được commit(cả stage và chưa stage), lưu chúng ở một chỗ khác để sử dụng sau này và sau đó khôi phục chúng từ bản sao làm việc của bạn.
    
    
    $ git status
    On branch master
    Changes to be committed:
    new file: style.css
    Changes not staged for commit:
    modified: index.html
    $ git stash
    Saved working directory and index state WIP on master: 5002d47 our new homepage
    HEAD is now at 5002d47 our new homepage
    $ git status
    On branch master
    nothing to commit, working tree clean
    

Chúng ta có thể sử dụng stash khi chúng ta phát hiện ra chúng ta đã quên điều gì đó trong
commit cuối cùng và đã bắt đầu làm việc tiếp theo trên nhánh đó:

    
    
    # Assume the latest commit was already done
    # start working on the next patch, and discovered I was missing something # stash away the current mess I made
    $ git stash save # some changes in the working dir # and now add them to the last commit:
    $ git add -u
    $ git commit --ammend # back to work!
    $ git stash pop
    

**Source:** [atlassian.com](https://www.atlassian.com/git/tutorials/saving-changes/git-stash)

### Q10: Làm thế nào để xóa một file khỏi git mà không cần xóa nó trong hệ thống file của bạn?

> Topic: **Git**  
Difficulty: ⭐⭐⭐⭐

Nếu bạn không cẩn thận trong khi sử dụng `git add`, bạn có thể sẽ thêm các tệp
bạn không muốn commit. Tuy nhiên, `git rm` sẽ xóa nó khỏi cả hai
vùng stage (chỉ mục), cũng như hệ thống file của bạn (working tree), có thể
không phải là những gì bạn muốn.

Thay vào đó sử dụng `git reset`:

    
    
    git reset filename # or
    echo filename >> .gitingore # add it to .gitignore to avoid re-adding it
    

Điều này có nghĩa là `git reset <paths>` trái ngược với `git add <paths>`.

**Source:** [codementor.io](https://www.codementor.io/citizen428/git-tutorial-10-common-git-problems-and-how-to-fix-them-aajv0katd)

### Q11: Khi nào sử dụng "git rebase" thay vì "git merge"?

> Topic: **Git**  
Difficulty: ⭐⭐⭐⭐⭐

Cả hai lệnh này được thiết kế để tích hợp các thay đổi từ một nhánh vào một nhánh khác - chỉ có điều chùng thực hiện theo những cách rất khác nhau.

Trước khi merge/rebase:

    
    
    A <- B <- C [master]
    ^ \ D <- E [branch]
    

sau khi `git merge master`:

    
    
    A <- B <- C
    ^ ^ \ \ D <- E <- F
    

Sau khi `git rebase master`:
```
A <- B <- C <- D <- E
```

Với rebase có thể nói là bạn đang sử dụng một nhánh làm cơ sở mới cho công việc của bạn.

**Khi nào sử dụng:**

  1. Nếu bạn chưa chắc chắn, sử dụng merge.
  2. Lựa chọn rebase hay merge tùy thuộc vào việc bạn muốn lịch sử trông như thế nào.

**Các yếu tố cần xem xét:**

  1. **Nhánh bạn có đang nhận được các thay đổi từ việc chia sẻ với các developer  khác bên ngoài nhóm của bạn (ví dụ: opensource, public) không?** Nếu có, đừng rebase. Rebase phá hủy nhánh và các developer đó sẽ có các repository bị hỏng / không nhất quán trừ khi họ sử dụng `git pull --rebase`.
  2. **Team development của bạn có kỹ năng nào?** Rebase là một hành động phá hoại. Điều đó có nghĩa, nếu bạn không áp dụng nó một cách chính xác, bạn có thể mất các công việc đã commit và hoặc phá vỡ sự thống nhất giữa các repository của các developer.
  3. **Bản thân nhánh đó có đại diện cho một thông tin hữu ích không?** Một số nhóm sử dụng mô hình `branch-per-feature`  nơi mà mỗi nhánh thể hiện một tính năng (hoặc bugfix hoặc tính năng con, ...). Trong mô hình này nhánh giúp xác định tập các commit liên quan. Trong trường hợp mô hình `branch-per-developer` chính nhánh không truyền tải bất cứ thông tin bổ sung nào (commit đã lưu tác giả). Sẽ không có hại gì khi rebase
  4. **Bạn có thể muốn revert một merge vì bất kỳ lý do nào?**  Revert (giống như undo) một rebase là một điều khá khó khăn và không thể (nếu rebase có xung đột) so với revert một merge. Nếu bạn nghĩ rằng có thể có một cơ hội bạn sẽ muốn revert thì sử dụng merge

**Source:** [stackoverflow.com](https://stackoverflow.com/questions/804115/when-do-you-use-git-rebase-instead-of-git-merge)

> _Thanks  for reading and good luck on your interview!_  
_Check more FullStack Interview Questions &amp; Answers on
[www.fullstack.cafe](https://www.fullstack.cafe/)_
