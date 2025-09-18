<script>
    export let name = "Abeer Younes";
    export let role = "Frontend Developer";
    export let avatar = "/avatar.png";
    export let bio = "Love building beautiful interfaces and drinking coffee";

    const flowers = [
        { id: 1, title: "HTML" },
        { id: 2, title: "CSS" },
        { id: 3, title: "JS · Node" },
        { id: 4, title: "SvelteKit" },
    ];
</script>

<div class="card">
    <div class="content">
        <h2>{name}</h2>
        <p class="role">{role}</p>
        <p class="bio">{bio}</p>
        <h3>skills</h3>
        <div class="garden">
            {#each flowers as f}
                <div
                    class="flower"
                    tabindex="0"
                    aria-label={`Flower showing ${f.title}`}
                >
                    <div class="petals" aria-hidden="true">
                        <svg viewBox="0 0 100 100" class="flower-svg">
                            <g transform="translate(50,50)">
                                <circle r="8" class="center" />
                                {#each Array(6) as _, i}
                                    <ellipse
                                        rx="12"
                                        ry="22"
                                        transform={`rotate(${i * 60}) translate(28,0)`}
                                        class="petal"
                                    />
                                {/each}
                            </g>
                        </svg>
                    </div>
                    <div class="label">{f.title}</div>
                </div>
            {/each}
        </div>
    </div>
    <div class="avatar-wrapper">
        <img class="avatar" src={avatar} alt="{name} avatar" />
    </div>
</div>

<style>
    :global(html),
    :global(body) {
        margin: 0;
        padding: 0;
        height: 100%;
        background-color: #ffffff;
        display: flex;
        justify-content: center;
        align-items: center;
        font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
    }

    .card {
        display: flex;
        align-items: center;
        gap: 2rem;
        margin: 2rem auto;
        border-radius: 12px;
        overflow: visible;
        background-color: #d9b4dc;
        font-family: monospace;
        color: #000000;
        max-width: 650px;
        min-height: 300px;
        padding: 2rem;
        position: relative;
        box-shadow: 0 0 15px #711667;
        animation: glow 2s ease-in-out infinite alternate;
        transition: transform 0.3s;
        flex-direction: column;
        justify-content: space-between;
    }

    @keyframes glow {
        0% {
            box-shadow:
                0 0 10px #711667,
                0 0 20px rgba(189, 108, 181, 0.5);
        }
        50% {
            box-shadow:
                0 0 20px #711667,
                0 0 40px rgba(56, 70, 50, 0.5);
        }
        100% {
            box-shadow:
                0 0 10px #711667,
                0 0 20px rgba(115, 163, 115, 0.5);
        }
    }

    .card:hover {
        transform: translateY(-8px);
    }

    .avatar-wrapper {
        display: inline-block;
        border-radius: 50%;
        overflow: hidden;
    }

 .avatar-wrapper:hover .avatar {
  box-shadow: 0 12px 30px rgba(0,0,0,0.35);
  transform: translateY(-4px);
}

    .avatar {
        width: 180px;
        object-fit: cover;
        border-radius: 50%;
        display: block;
        transition: box-shadow 0.25s ease, transform 0.25s ease;
    }

    .content {
        flex: 1;
        text-align: center;
        z-index: 1;
        position: relative;
    }

    h2 {
        margin: 0.3rem 0;
        font-size: 2rem;
        margin-bottom: 1rem;
        color: #4b0082;
    }

    h3 {
        font-size: 1.30rem;
        margin-bottom: 1rem;
        color: #1e3a8a;
    }

    p.role {
        margin: 0;
        font-size: 1.1rem;
    }
    p.bio {
        font-size: 1rem;
        margin-top: 0.5rem;
    }

    .garden {
        margin-top: 1.5rem;
        display: flex;
        justify-content: center;
        gap: 12px;
        flex-wrap: wrap;
    }
    .flower {
        width: 90px;
        height: 90px;
        border-radius: 12px;
        display: flex;
        align-items: center;
        justify-content: center;
        position: relative;
        background: linear-gradient(180deg, #fff, #f1f5f9);
        box-shadow: 0 4px 12px rgba(2, 6, 23, 0.08);
        cursor: pointer;
        transition: transform 0.18s ease;
        outline: none;
    }
    .flower:focus {
        box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.14);
        transform: translateY(-4px);
    }
    .flower:active {
        transform: translateY(0);
    }

    .flower-svg {
        width: 60px;
        height: 60px;
    }
    .petal {
        fill: #ff7aa2;
        opacity: 0.95;
        transition:
            transform 0.36s cubic-bezier(0.2, 0.9, 0.3, 1),
            opacity 0.25s ease;
    }
    .center {
        fill: #ffd166;
    }

    .petals {
        display: flex;
        align-items: center;
        justify-content: center;
        transition:
            opacity 0.28s ease,
            transform 0.28s ease;
    }
    .label {
        position: absolute;
        inset: 0;
        display: flex;
        align-items: center;
        justify-content: center;
        font-weight: 700;
        font-size: 14px;
        letter-spacing: 0.4px;
        opacity: 0;
        transform: translateY(8px) scale(0.95);
        transition:
            opacity 0.22s ease,
            transform 0.22s cubic-bezier(0.2, 0.9, 0.3, 1);
        pointer-events: none;
    }

    .flower:hover .petals,
    .flower:focus .petals {
        opacity: 0;
        transform: scale(0.6) translateY(-6px);
    }
    .flower:hover .label,
    .flower:focus .label {
        opacity: 1;
        transform: translateY(0) scale(1);
    }

    @media (max-width: 500px) {
        .card {
            padding: 1rem;
            min-height: 250px;
        }
        .avatar {
            width: 140px;
            height: 140px;
        }
        .flower {
            width: 70px;
            height: 70px;
        }
        .flower-svg {
            width: 45px;
            height: 45px;
        }
    }
</style>
