let posts = JSON.parse(localStorage.getItem("posts")) || [];

const titleInput = document.getElementById("title");
const contentInput = document.getElementById("content");
const publishBtn = document.getElementById("publishBtn");
const postsDiv = document.getElementById("posts");

function savePosts() {
    localStorage.setItem("posts", JSON.stringify(posts));
}

function displayPosts() {

    postsDiv.innerHTML = "";

    posts.forEach((post, index) => {

        const postDiv = document.createElement("div");
        postDiv.className = "post";

        let commentsHTML = "";

        post.comments.forEach((comment, cIndex) => {
            commentsHTML += `
            <li>
                ${comment}
                <button class="delete-btn"
                onclick="deleteComment(${index}, ${cIndex})">
                Delete
                </button>
            </li>
            `;
        });

        postDiv.innerHTML = `
            <h3>${post.title}</h3>

            <p>${post.content}</p>

            <button onclick="deletePost(${index})">
                Delete Post
            </button>

            <hr>

            <input
            class="comment-input"
            id="comment-${index}"
            placeholder="Write a comment">

            <button onclick="addComment(${index})">
                Add Comment
            </button>

            <ul class="comment-list">
                ${commentsHTML}
            </ul>
        `;

        postsDiv.appendChild(postDiv);

    });

}

publishBtn.onclick = function () {

    let title = titleInput.value.trim();
    let content = contentInput.value.trim();

    if (title === "" || content === "") {
        alert("Please enter title and content.");
        return;
    }

    posts.unshift({
        title: title,
        content: content,
        comments: []
    });

    savePosts();

    displayPosts();

    titleInput.value = "";
    contentInput.value = "";

};

function deletePost(index) {

    posts.splice(index, 1);

    savePosts();

    displayPosts();

}

function addComment(index) {

    let input = document.getElementById("comment-" + index);

    let comment = input.value.trim();

    if (comment === "") return;

    posts[index].comments.push(comment);

    savePosts();

    displayPosts();

}

function deleteComment(postIndex, commentIndex) {

    posts[postIndex].comments.splice(commentIndex, 1);

    savePosts();

    displayPosts();

}

displayPosts();
