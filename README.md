<h2>Hiii :3</h2>

#include "me.with.u"
<!---
Putra3340/Putra3340 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
function fetchConfig() {
            fetch('https://putrartx.my.id/Api/BackendSharp.php')
                .then(response => response.json())
                .then(data => {
                    if (data.error) {
                        document.getElementById('output').innerHTML = '<p class="card-text">Discord Presence is Offline</p>';
                    } else {
                        document.getElementById('output').innerHTML = `
                            <div class="d-flex align-items-start gap-2">
                                ${data.img !== "0" ? `<img src="${data.img}" alt="Activity Icon" style="width: 80px; height: 80px; border-radius: 8px;">` : ''}
                                <div class="flex-grow-1" style="margin-left: 4px">
                                    ${data.status !== "0" ? `<h6 class="card-title mb-1" style="font-size: 14px; font-weight: 600;">${
                                        data.status === "Online" ? "🟢 Online" :
                                        data.status === "Idle" ? "🟠 Idle" :
                                        data.status === "Do Not Disturb" ? "🔴 Do Not Disturb" :
                                        data.status === "Offline" ? "⚫ Offline" :
                                        data.status
                                    }</h6>` : ''}
                                    ${data.name !== "0" ? `<p class="card-text mb-1" style="font-size: 12px; color: #dcddde;">${data.name}</p>` : ''}
                                    ${data.desc1 !== "0" ? `<p style="font-size: 11px; color: #b9bbbe; margin-bottom: 1px;">${data.desc1}</p>` : ''}
                                    ${data.desc2 && data.desc2 !== "0" ? `<p style="font-size: 11px; color: #b9bbbe; margin-bottom: 1px;">${data.desc2}</p>` : ''}
                                    ${data.jam !== "0" ? `<p class="card-text mb-0" style="font-size: 11px; color: #b9bbbe;">${data.jam}${data.jam_end !== "0" ? ` --- ${data.jam_end}` : ''}</p>` : ''}
                                </div>
                            </div>
                        `;
                    }
                })
                .catch(error => {
                    document.getElementById('output').innerHTML = '<p class="card-text">Discord Presence is Offline</p>';
                });
        }

        // Fetch every second
        setInterval(fetchConfig, 1000);

        // Fetch on page load
        window.onload = fetchConfig;
